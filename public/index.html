import React, { useState, useEffect } from 'react';
import { Calendar, Users, Plus, Save, Sparkles } from 'lucide-react';

const AnestheticScheduler = () => {
  const [currentView, setCurrentView] = useState('overview');
  const [selectedDate, setSelectedDate] = useState('2025-10-16');
  const [selectedWeek, setSelectedWeek] = useState('B');
  const [saveStatus, setSaveStatus] = useState('');
  
  const allocationTypes = ['Leave', 'Sick Leave', 'Release', 'Admin', 'W-end Release', 'OT PCR', 'PCR Worked', 'FRL', 'Congress'];
  const callLevels = ['', '1st', '2nd', '3rd'];
  const statusOptions = ['Pending', 'Confirmed', 'Cancelled', 'Nil'];
  
  const [doctors, setDoctors] = useState([
    { id: 1, name: 'Dr Bhagwan', allocations: {} },
    { id: 2, name: 'Dr Buley', allocations: {} },
    { id: 3, name: 'Dr Franz', allocations: {} },
    { id: 4, name: 'Dr Gordon', allocations: {} },
    { id: 5, name: 'Dr Jones', allocations: {} },
    { id: 6, name: 'Dr Madurai', allocations: {} },
    { id: 7, name: 'Dr Mitchell', allocations: {} },
    { id: 8, name: 'Dr Naidoo', allocations: {} },
    { id: 9, name: 'Dr Paterson', allocations: {} },
    { id: 10, name: 'Dr Slabber', allocations: {} },
    { id: 11, name: 'Dr Swart', allocations: {} },
    { id: 12, name: 'Dr von Rahden', allocations: {} }
  ]);
  
  const [surgeons, setSurgeons] = useState([
    { id: 1, name: 'Dr Pavlov', electives: [{ week: 'B', day: 'Thursday', time: '08h00-12h30', session: 'morning', hospital: 'st_annes' }] },
    { id: 2, name: 'Dr K.Chetty', electives: [] }
  ]);
  
  const hospitals = [
    { id: 'st_annes', name: "ST ANNE'S" },
    { id: 'mdc', name: 'MDC' },
    { id: 'mediclinic', name: 'MEDICLINIC' },
    { id: 'hilton', name: 'HILTON' }
  ];
  
  const [schedule, setSchedule] = useState({ morning: {}, afternoon: {} });
  const [allSchedules, setAllSchedules] = useState({});
  
  const getDayOfWeek = (date) => {
    return ['Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday'][new Date(date).getDay()];
  };
  
  const initSchedule = () => {
    const newSched = { morning: {}, afternoon: {} };
    const day = getDayOfWeek(selectedDate);
    hospitals.forEach(h => {
      newSched.morning[h.id] = [];
      newSched.afternoon[h.id] = [];
    });
    surgeons.forEach(s => {
      s.electives.forEach(e => {
        if (e.week === selectedWeek && e.day === day) {
          newSched[e.session][e.hospital].push({
            surgeon: s.name, time: e.time, anaesthetist: '', notes: '', cases: 0, status: 'Pending', isElective: true
          });
        }
      });
    });
    return newSched;
  };
  
  useEffect(() => {
    const saved = localStorage.getItem('sched_data');
    if (saved) {
      try {
        const data = JSON.parse(saved);
        if (data.schedules) setAllSchedules(data.schedules);
        if (data.doctors) setDoctors(data.doctors);
        if (data.surgeons) setSurgeons(data.surgeons);
      } catch (e) {}
    }
  }, []);
  
  useEffect(() => {
    if (allSchedules[selectedDate]) {
      setSchedule(allSchedules[selectedDate]);
    } else {
      setSchedule(initSchedule());
    }
  }, [selectedDate, selectedWeek]);
  
  const save = () => {
    const newSchedules = { ...allSchedules, [selectedDate]: schedule };
    setAllSchedules(newSchedules);
    localStorage.setItem('sched_data', JSON.stringify({ schedules: newSchedules, doctors, surgeons }));
    setSaveStatus('saved');
    setTimeout(() => setSaveStatus(''), 2000);
  };
  
  const updateAlloc = (docId, date, session, type) => {
    setDoctors(prev => prev.map(d => {
      if (d.id === docId) {
        const a = { ...d.allocations };
        if (!a[date]) a[date] = {};
        a[date][session] = type;
        return { ...d, allocations: a };
      }
      return d;
    }));
    setTimeout(save, 100);
  };
  
  const getAlloc = (name, date, session) => {
    const doc = doctors.find(d => d.name === name);
    return doc?.allocations?.[date]?.[session] || '';
  };
  
  const getCall = (name, date) => {
    const doc = doctors.find(d => d.name === name);
    return doc?.allocations?.[date]?.call || '';
  };
  
  const setCall = (docId, date, call) => {
    setDoctors(prev => prev.map(d => {
      if (d.id === docId) {
        const a = { ...d.allocations };
        if (!a[date]) a[date] = {};
        a[date].call = call;
        return { ...d, allocations: a };
      }
      return d;
    }));
    setTimeout(save, 100);
  };
  
  const getAutoAlloc = (name) => {
    const c = getCall(name, selectedDate);
    const am = getAlloc(name, selectedDate, 'morning');
    const pm = getAlloc(name, selectedDate, 'afternoon');
    const items = [];
    if (c) items.push(c);
    if (am === 'OT PCR' || pm === 'OT PCR') items.push('OT PCR');
    if (am === 'Release' || pm === 'Release') items.push('Release');
    return items.join(', ');
  };
  
  const getAvailableDoctors = (session) => {
    return doctors.filter(d => {
      const alloc = getAlloc(d.name, selectedDate, session);
      return alloc !== 'Leave' && alloc !== 'Sick Leave' && alloc !== 'Release' && alloc !== 'W-end Release';
    });
  };
  
  const addSlot = (sess, hosp) => {
    setSchedule(prev => ({
      ...prev,
      [sess]: {
        ...prev[sess],
        [hosp]: [...(prev[sess][hosp] || []), { surgeon: '', time: '', anaesthetist: '', notes: '', cases: 0, status: 'Pending', isElective: false }]
      }
    }));
  };
  
  const updateSlot = (sess, hosp, idx, field, val) => {
    setSchedule(prev => ({
      ...prev,
      [sess]: {
        ...prev[sess],
        [hosp]: prev[sess][hosp].map((s, i) => i === idx ? { ...s, [field]: val } : s)
      }
    }));
  };
  
  const removeSlot = (sess, hosp, idx) => {
    if (schedule[sess][hosp][idx].isElective) {
      alert('Cannot remove elective slots');
      return;
    }
    setSchedule(prev => ({
      ...prev,
      [sess]: {
        ...prev[sess],
        [hosp]: prev[sess][hosp].filter((_, i) => i !== idx)
      }
    }));
  };
  
  const getColor = (alloc) => {
    if (!alloc) return 'bg-white border-2 border-gray-200';
    if (alloc === 'Leave' || alloc === 'Sick Leave') return 'bg-red-500 text-white';
    if (alloc === 'Release' || alloc === 'W-end Release') return 'bg-blue-400 text-white';
    if (alloc === 'OT PCR' || alloc === 'PCR Worked') return 'bg-orange-400 text-white';
    return 'bg-purple-400 text-white';
  };
  
  return (
    <div className="min-h-screen bg-gradient-to-br from-slate-50 via-blue-50 to-indigo-50 p-6">
      <div className="max-w-7xl mx-auto">
        <div className="bg-white rounded-3xl shadow-2xl p-8 mb-6">
          <div className="flex justify-between items-center mb-6">
            <div className="flex items-center gap-4">
              <div className="bg-gradient-to-br from-blue-600 to-indigo-600 p-4 rounded-2xl">
                <Sparkles className="text-white" size={32} />
              </div>
              <div>
                <h1 className="text-4xl font-bold bg-gradient-to-r from-blue-600 to-indigo-600 bg-clip-text text-transparent">
                  Daily Allocation
                </h1>
                <p className="text-gray-500 text-sm">Anaesthetic Partner Scheduling</p>
              </div>
            </div>
            <div className="text-right">
              <div className="text-sm font-semibold">{new Date(selectedDate).toLocaleDateString()}</div>
              <div className="text-xs text-gray-500">Week {selectedWeek}</div>
            </div>
          </div>
          
          <div className="flex gap-4 mb-6 flex-wrap">
            <input type="date" value={selectedDate} onChange={(e) => setSelectedDate(e.target.value)} 
              className="border-2 px-4 py-2 rounded-xl" />
            <select value={selectedWeek} onChange={(e) => setSelectedWeek(e.target.value)} 
              className="border-2 px-4 py-2 rounded-xl">
              <option value="A">Week A</option>
              <option value="B">Week B</option>
            </select>
            <button onClick={save} 
              className="bg-gradient-to-r from-green-500 to-emerald-600 text-white px-6 py-2 rounded-xl flex items-center gap-2">
              <Save size={18} /> {saveStatus === 'saved' ? 'Saved!' : 'Save'}
            </button>
          </div>
          
          <div className="flex gap-3">
            <button onClick={() => setCurrentView('overview')} 
              className={`px-5 py-2 rounded-xl font-medium text-sm ${currentView === 'overview' ? 'bg-blue-600 text-white' : 'bg-gray-100'}`}>
              Overview
            </button>
            <button onClick={() => setCurrentView('schedule')} 
              className={`px-5 py-2 rounded-xl font-medium text-sm ${currentView === 'schedule' ? 'bg-blue-600 text-white' : 'bg-gray-100'}`}>
              Schedule
            </button>
            <button onClick={() => setCurrentView('surgeons')} 
              className={`px-5 py-2 rounded-xl font-medium text-sm ${currentView === 'surgeons' ? 'bg-blue-600 text-white' : 'bg-gray-100'}`}>
              Surgeons
            </button>
          </div>
        </div>
        
        <div className="bg-white rounded-3xl shadow-2xl p-8">
          {currentView === 'overview' && (
            <div>
              <h2 className="text-2xl font-bold mb-4">Daily Allocation Overview</h2>
              <div className="overflow-x-auto">
                <table className="w-full border-2">
                  <thead>
                    <tr className="bg-gray-800 text-white">
                      <th className="p-3 text-left">Doctor</th>
                      <th className="p-3">Call</th>
                      <th className="p-3">AM</th>
                      <th className="p-3">PM</th>
                    </tr>
                  </thead>
                  <tbody>
                    {doctors.map((d, i) => {
                      const am = getAlloc(d.name, selectedDate, 'morning');
                      const pm = getAlloc(d.name, selectedDate, 'afternoon');
                      const call = getCall(d.name, selectedDate);
                      return (
                        <tr key={d.id} className={i % 2 === 0 ? 'bg-white' : 'bg-gray-50'}>
                          <td className="p-3 font-semibold">{d.name}</td>
                          <td className="p-2 text-center">
                            <select value={call} onChange={(e) => setCall(d.id, selectedDate, e.target.value)}
                              className="px-3 py-2 rounded-xl border-2">
                              {callLevels.map(c => <option key={c} value={c}>{c || '-'}</option>)}
                            </select>
                          </td>
                          <td className="p-2 text-center">
                            <select value={am} onChange={(e) => updateAlloc(d.id, selectedDate, 'morning', e.target.value)}
                              className={`px-4 py-2 rounded-xl min-w-[140px] ${getColor(am)}`}>
                              <option value="">-</option>
                              {allocationTypes.map(t => <option key={t} value={t}>{t}</option>)}
                            </select>
                          </td>
                          <td className="p-2 text-center">
                            <select value={pm} onChange={(e) => updateAlloc(d.id, selectedDate, 'afternoon', e.target.value)}
                              className={`px-4 py-2 rounded-xl min-w-[140px] ${getColor(pm)}`}>
                              <option value="">-</option>
                              {allocationTypes.map(t => <option key={t} value={t}>{t}</option>)}
                            </select>
                          </td>
                        </tr>
                      );
                    })}
                  </tbody>
                </table>
              </div>
            </div>
          )}
          
          {currentView === 'schedule' && (
            <div>
              {['morning', 'afternoon'].map(sess => (
                <div key={sess} className="mb-6">
                  <h3 className="text-xl font-bold bg-gray-800 text-white p-3 rounded-t-xl">
                    {sess === 'morning' ? '🌅 Morning' : '🌆 Afternoon'}
                  </h3>
                  <div className="border-2 rounded-b-xl overflow-x-auto">
                    <table className="w-full">
                      <thead>
                        <tr className="bg-gray-100">
                          <th className="p-2 text-left">Hospital</th>
                          <th className="p-2 text-left">Surgeon</th>
                          <th className="p-2 text-left">Time</th>
                          <th className="p-2 text-left">Anaesthetist</th>
                          <th className="p-2 text-left">Allocation</th>
                          <th className="p-2 text-left">Notes</th>
                          <th className="p-2 text-left">Cases</th>
                          <th className="p-2 text-left">Status</th>
                          <th className="p-2">Action</th>
                        </tr>
                      </thead>
                      <tbody>
                        {hospitals.map(h => {
                          const slots = schedule[sess][h.id] || [];
                          return slots.map((slot, idx) => (
                            <tr key={`${h.id}-${idx}`} className="border-b">
                              <td className="p-2 font-bold">
                                {h.name}
                                {slot.isElective && <span className="ml-2 text-xs bg-blue-500 text-white px-2 py-0.5 rounded">ELECTIVE</span>}
                              </td>
                              <td className="p-2">
                                {slot.isElective ? (
                                  <div className="px-3 py-2 bg-gray-100 rounded">{slot.surgeon}</div>
                                ) : (
                                  <select value={slot.surgeon} onChange={(e) => updateSlot(sess, h.id, idx, 'surgeon', e.target.value)} 
                                    className="w-full p-2 border-2 rounded">
                                    <option value="">Select...</option>
                                    {surgeons.map(s => <option key={s.id} value={s.name}>{s.name}</option>)}
                                  </select>
                                )}
                              </td>
                              <td className="p-2">
                                <input type="text" value={slot.time} onChange={(e) => updateSlot(sess, h.id, idx, 'time', e.target.value)} 
                                  className="w-full p-2 border-2 rounded" />
                              </td>
                              <td className="p-2">
                                <select value={slot.anaesthetist} onChange={(e) => updateSlot(sess, h.id, idx, 'anaesthetist', e.target.value)} 
                                  className="w-full p-2 border-2 rounded">
                                  <option value="">Select...</option>
                                  {getAvailableDoctors(sess).map(d => <option key={d.id} value={d.name}>{d.name}</option>)}
                                </select>
                              </td>
                              <td className="p-2">
                                <div className="px-3 py-2 bg-blue-50 rounded text-xs text-blue-800">
                                  {slot.anaesthetist ? getAutoAlloc(slot.anaesthetist) || '-' : '-'}
                                </div>
                              </td>
                              <td className="p-2">
                                <input type="text" value={slot.notes} onChange={(e) => updateSlot(sess, h.id, idx, 'notes', e.target.value)} 
                                  className="w-full p-2 border-2 rounded" />
                              </td>
                              <td className="p-2">
                                <input type="number" value={slot.cases} onChange={(e) => updateSlot(sess, h.id, idx, 'cases', parseInt(e.target.value) || 0)} 
                                  className="w-full p-2 border-2 rounded" min="0" />
                              </td>
                              <td className="p-2">
                                <select value={slot.status} onChange={(e) => updateSlot(sess, h.id, idx, 'status', e.target.value)} 
                                  className="w-full p-2 border-2 rounded">
                                  {statusOptions.map(s => <option key={s} value={s}>{s}</option>)}
                                </select>
                              </td>
                              <td className="p-2 text-center">
                                <button onClick={() => removeSlot(sess, h.id, idx)} className="text-red-500 hover:text-red-700">✕</button>
                              </td>
                            </tr>
                          ));
                        })}
                      </tbody>
                    </table>
                  </div>
                  <div className="flex gap-2 mt-2">
                    {hospitals.map(h => (
                      <button key={h.id} onClick={() => addSlot(sess, h.id)} 
                        className="text-sm border-2 border-blue-300 px-3 py-1 rounded-xl text-blue-600">
                        + {h.name}
                      </button>
                    ))}
                  </div>
                </div>
              ))}
            </div>
          )}
          
          {currentView === 'surgeons' && (
            <div>
              <h2 className="text-2xl font-bold mb-4">Surgeon & Elective Management</h2>
              
              <div className="mb-6 p-4 bg-blue-50 rounded-xl border-2 border-blue-200">
                <h3 className="font-bold mb-2">Add New Surgeon</h3>
                <div className="flex gap-3">
                  <input 
                    type="text" 
                    placeholder="Enter surgeon name (e.g., Dr Smith)"
                    className="flex-1 px-4 py-2 border-2 rounded-xl"
                    id="newSurgeonInput"
                  />
                  <button 
                    onClick={() => {
                      const input = document.getElementById('newSurgeonInput');
                      if (input.value.trim()) {
                        setSurgeons(prev => [...prev, { id: Date.now(), name: input.value.trim(), electives: [] }]);
                        input.value = '';
                        setTimeout(save, 100);
                      }
                    }}
                    className="bg-blue-600 text-white px-6 py-2 rounded-xl flex items-center gap-2">
                    <Plus size={18} /> Add Surgeon
                  </button>
                </div>
              </div>
              
              <div className="space-y-4">
                {surgeons.map(surgeon => (
                  <div key={surgeon.id} className="border-2 rounded-xl p-6">
                    <div className="flex justify-between mb-4">
                      <div>
                        <h3 className="font-bold text-xl">{surgeon.name}</h3>
                        <p className="text-sm text-gray-500">{surgeon.electives.length} elective slot(s)</p>
                      </div>
                      <button onClick={() => {
                        if (window.confirm(`Remove ${surgeon.name}?`)) {
                          setSurgeons(prev => prev.filter(s => s.id !== surgeon.id));
                          setTimeout(save, 100);
                        }
                      }} className="text-red-500">Remove</button>
                    </div>
                    
                    <button onClick={() => {
                      setSurgeons(prev => prev.map(s => {
                        if (s.id === surgeon.id) {
                          return { ...s, electives: [...s.electives, { week: 'A', day: 'Monday', time: '08h00-12h30', session: 'morning', hospital: 'st_annes' }] };
                        }
                        return s;
                      }));
                      setTimeout(save, 100);
                    }} className="border-2 border-blue-300 px-4 py-2 rounded-lg text-blue-600 mb-3">
                      <Plus size={16} className="inline" /> Add Elective
                    </button>
                    
                    {surgeon.electives.map((el, idx) => (
                      <div key={idx} className="bg-gray-50 p-3 rounded-lg mb-2">
                        <div className="grid grid-cols-6 gap-2">
                          <select value={el.week} onChange={(e) => {
                            setSurgeons(prev => prev.map(s => s.id === surgeon.id ? { ...s, electives: s.electives.map((e, i) => i === idx ? { ...e, week: e.target.value } : e) } : s));
                            setTimeout(save, 100);
                          }} className="p-2 border-2 rounded">
                            <option value="A">Week A</option>
                            <option value="B">Week B</option>
                          </select>
                          <select value={el.day} onChange={(e) => {
                            setSurgeons(prev => prev.map(s => s.id === surgeon.id ? { ...s, electives: s.electives.map((e, i) => i === idx ? { ...e, day: e.target.value } : e) } : s));
                            setTimeout(save, 100);
                          }} className="p-2 border-2 rounded">
                            {['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday'].map(d => <option key={d} value={d}>{d}</option>)}
                          </select>
                          <input type="text" value={el.time} className="p-2 border-2 rounded" />
                          <select value={el.session} className="p-2 border-2 rounded">
                            <option value="morning">Morning</option>
                            <option value="afternoon">Afternoon</option>
                          </select>
                          <select value={el.hospital} className="p-2 border-2 rounded">
                            {hospitals.map(h => <option key={h.id} value={h.id}>{h.name}</option>)}
                          </select>
                          <button onClick={() => {
                            setSurgeons(prev => prev.map(s => s.id === surgeon.id ? { ...s, electives: s.electives.filter((_, i) => i !== idx) } : s));
                            setTimeout(save, 100);
                          }} className="text-red-500">✕</button>
                        </div>
                      </div>
                    ))}
                  </div>
                ))}
              </div>
            </div>
          )}
        </div>
      </div>
    </div>
  );
};

export default AnestheticScheduler;
