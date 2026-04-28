import { useState, useEffect, useMemo } from "react";

// ═══════════════════════════════════════════════════════════════
//  CONSTANTS
// ═══════════════════════════════════════════════════════════════
const WILAYAS = ["أدرار","الشلف","الأغواط","أم البواقي","باتنة","بجاية","بسكرة","بشار","البليدة","البويرة","تمنراست","تبسة","تلمسان","تيارت","تيزي وزو","الجزائر","الجلفة","جيجل","سطيف","سعيدة","سكيكدة","سيدي بلعباس","عنابة","قالمة","قسنطينة","المدية","مستغانم","المسيلة","معسكر","ورقلة","وهران","البيض","إليزي","برج بوعريريج","بومرداس","الطارف","تندوف","تيسمسيلت","الوادي","خنشلة","سوق أهراس","تيبازة","ميلة","عين الدفلى","النعامة","عين تيموشنت","غرداية","غليزان","تيميمون","طولقة","بني عباس","أولاد جلال","بريكة","أريس","تقرت","جانت","المغير","المنيعة"];
const REGIONS = ["الشرق","الوسط","الغرب","الشمال","الجنوب"];
const COLOR_TYPES = ["مسحوق","سائل","حبيبات"];
const TRADE_TYPES = ["نفخ بلاستيك","حقن بلاستيك","تغليف","قولبة دورانية","أخرى"];
const SUPPLIER_TYPES = ["منتج محلي","منتج مستورد"];
const PRIORITIES = ["الجودة","السعر","التوفير","أخرى"];
const QUANTITY_RANGES = ["من 25 كغ الى 975 كغ","من 1000 كغ الى 4975 كغ","من 5000 كغ الى 19000 كغ","أكثر من 19000 كغ"];
const OPINIONS = ["هل اعجبته العلامة","هل سبق له تجريب","مهتم بعلامتنا"];
const CLIENT_STATUS = ["نشط","غير نشط","مهتم بعملنا"];
const STOCK_STATUS = ["متوفرة","غير متوفرة","كمية قليلة","في تصنيع"];
const EXPENSE_TYPES = ["تنقل","أكل","وقود","مبيت","كل شيئ مع بعض"];
const COLORS_LIST = ["أبيض","أسود","أصفر","ذهبي","أحمر","برتقالي","وردي","أزرق","أخضر","بنفسجي","بني","بيج","رمادي","فضي"];
const VISIT_SUCCESS = ["ناجحة","غير ناجحة","مهتم بعملنا"];

function useLS(key, def) {
  const [val, setVal] = useState(() => {
    try { const s = localStorage.getItem(key); return s ? JSON.parse(s) : def; } catch { return def; }
  });
  useEffect(() => { try { localStorage.setItem(key, JSON.stringify(val)); } catch {} }, [key, val]);
  return [val, setVal];
}

function uid(prefix) { return prefix + Date.now().toString(36).toUpperCase(); }

const PIE_COLORS = ["#D4A017","#E8C55A","#F0D890","#A07810","#7A5A08","#C49010","#F8E4A0","#B08820"];

function PieChart({ data, size = 160 }) {
  if (!data || data.length === 0) return <div style={{color:"#888",textAlign:"center",padding:"20px",fontSize:"13px"}}>لا توجد بيانات</div>;
  const total = data.reduce((s, d) => s + d.value, 0);
  if (total === 0) return <div style={{color:"#888",textAlign:"center",padding:"20px",fontSize:"13px"}}>لا توجد بيانات</div>;
  let cum = 0;
  const slices = data.map((d, i) => {
    const pct = d.value / total;
    const start = cum; cum += pct;
    const a1 = start * 2 * Math.PI - Math.PI / 2;
    const a2 = cum * 2 * Math.PI - Math.PI / 2;
    const r = size / 2 - 10;
    const cx = size / 2, cy = size / 2;
    const x1 = cx + r * Math.cos(a1), y1 = cy + r * Math.sin(a1);
    const x2 = cx + r * Math.cos(a2), y2 = cy + r * Math.sin(a2);
    const large = pct > 0.5 ? 1 : 0;
    return { path: `M${cx},${cy} L${x1},${y1} A${r},${r} 0 ${large},1 ${x2},${y2} Z`, color: PIE_COLORS[i % PIE_COLORS.length], label: d.label, value: d.value, pct: Math.round(pct * 100) };
  });
  return (
    <div style={{display:"flex",alignItems:"center",gap:"16px",flexWrap:"wrap"}}>
      <svg width={size} height={size}>
        {slices.map((s, i) => <path key={i} d={s.path} fill={s.color} stroke="#0a0a0a" strokeWidth="2"/>)}
        <circle cx={size/2} cy={size/2} r={size/6} fill="#0d0d0d"/>
      </svg>
      <div style={{display:"flex",flexDirection:"column",gap:"6px"}}>
        {slices.map((s, i) => (
          <div key={i} style={{display:"flex",alignItems:"center",gap:"8px",fontSize:"12px",color:"#ccc"}}>
            <div style={{width:10,height:10,borderRadius:"50%",background:s.color,flexShrink:0}}/>
            <span>{s.label}</span>
            <span style={{color:PIE_COLORS[i%PIE_COLORS.length],fontWeight:"bold"}}>{s.value} ({s.pct}%)</span>
          </div>
        ))}
      </div>
    </div>
  );
}

// ═══════════════════════════════════════════════════════════════
//  MAIN APP
// ═══════════════════════════════════════════════════════════════
export default function App() {
  const [page, setPage] = useState(0);
  const [products, setProducts] = useLS("fc_products", []);
  const [clients, setClients] = useLS("fc_clients", []);
  const [visits, setVisits] = useLS("fc_visits", []);
  const [orders, setOrders] = useLS("fc_orders", []);
  const [expenses, setExpenses] = useLS("fc_expenses", []);
  const [goals, setGoals] = useLS("fc_goals", { monthly: 20, revenue: 500000, visitTarget: 30, successRate: 70, newClients: 5, note: "" });

  const pages = ["الرئيسية","العملاء","المنتجات","الزيارات","الطلبات","البيلان","المصاريف","الأداء"];

  const S = {
    app: { minHeight:"100vh", background:"#080808", color:"#e8d5a0", fontFamily:"'Cairo', sans-serif", direction:"rtl" },
    header: { background:"linear-gradient(135deg,#1a1400 0%,#0d0d00 50%,#0a0800 100%)", borderBottom:"1px solid #3a2e00", padding:"0 24px", display:"flex", alignItems:"center", justifyContent:"space-between", position:"sticky", top:0, zIndex:100, height:"64px" },
    logo: { fontSize:"22px", fontWeight:"900", letterSpacing:"2px", color:"#D4A017", textShadow:"0 0 30px #D4A01766" },
    sub: { fontSize:"11px", color:"#888", letterSpacing:"3px", textTransform:"uppercase" },
    nav: { display:"flex", gap:"4px", overflowX:"auto" },
    navBtn: (active) => ({ padding:"8px 14px", borderRadius:"8px", border:"none", cursor:"pointer", fontSize:"13px", fontWeight:"700", fontFamily:"'Cairo',sans-serif", background: active ? "linear-gradient(135deg,#D4A017,#A07810)" : "transparent", color: active ? "#000" : "#888", transition:"all 0.2s", whiteSpace:"nowrap" }),
    body: { padding:"24px", maxWidth:"1400px", margin:"0 auto" },
    card: { background:"#111008", border:"1px solid #2a2200", borderRadius:"16px", padding:"20px", marginBottom:"20px" },
    cardGold: { background:"linear-gradient(135deg,#1a1400,#0f0c00)", border:"1px solid #D4A01733", borderRadius:"16px", padding:"20px", marginBottom:"20px" },
    title: { fontSize:"20px", fontWeight:"900", color:"#D4A017", marginBottom:"16px", borderBottom:"1px solid #2a2200", paddingBottom:"10px" },
    label: { display:"block", fontSize:"12px", color:"#888", marginBottom:"4px", fontWeight:"600" },
    input: { width:"100%", background:"#0d0d00", border:"1px solid #2a2200", borderRadius:"8px", padding:"10px 12px", color:"#e8d5a0", fontSize:"13px", fontFamily:"'Cairo',sans-serif", outline:"none", boxSizing:"border-box" },
    select: { width:"100%", background:"#0d0d00", border:"1px solid #2a2200", borderRadius:"8px", padding:"10px 12px", color:"#e8d5a0", fontSize:"13px", fontFamily:"'Cairo',sans-serif", outline:"none", boxSizing:"border-box" },
    btn: { background:"linear-gradient(135deg,#D4A017,#A07810)", color:"#000", border:"none", borderRadius:"8px", padding:"10px 20px", fontFamily:"'Cairo',sans-serif", fontWeight:"900", fontSize:"13px", cursor:"pointer" },
    btnDanger: { background:"#3a0808", color:"#ff6666", border:"1px solid #660000", borderRadius:"6px", padding:"6px 12px", fontFamily:"'Cairo',sans-serif", fontSize:"12px", cursor:"pointer" },
    btnGhost: { background:"transparent", color:"#D4A017", border:"1px solid #D4A01744", borderRadius:"8px", padding:"8px 16px", fontFamily:"'Cairo',sans-serif", fontSize:"13px", cursor:"pointer" },
    grid2: { display:"grid", gridTemplateColumns:"1fr 1fr", gap:"12px" },
    grid3: { display:"grid", gridTemplateColumns:"1fr 1fr 1fr", gap:"12px" },
    grid4: { display:"grid", gridTemplateColumns:"repeat(4,1fr)", gap:"12px" },
    table: { width:"100%", borderCollapse:"collapse", fontSize:"13px" },
    th: { background:"#1a1400", color:"#D4A017", padding:"10px 12px", textAlign:"right", fontWeight:"700", borderBottom:"1px solid #2a2200" },
    td: { padding:"10px 12px", borderBottom:"1px solid #1a1400", color:"#ccc", verticalAlign:"middle" },
    stat: { background:"#0d0c00", border:"1px solid #2a2200", borderRadius:"12px", padding:"16px", textAlign:"center" },
    statNum: { fontSize:"28px", fontWeight:"900", color:"#D4A017" },
    statLabel: { fontSize:"12px", color:"#888", marginTop:"4px" },
    badge: (c) => ({ display:"inline-block", padding:"3px 10px", borderRadius:"20px", fontSize:"11px", fontWeight:"700",
      background: c==="نشط"||c==="ناجحة"||c==="متوفرة" ? "#0a2200" : c==="مهتم بعملنا" ? "#1a1000" : "#1a0000",
      color: c==="نشط"||c==="ناجحة"||c==="متوفرة" ? "#44ff88" : c==="مهتم بعملنا" ? "#D4A017" : "#ff4444",
      border: `1px solid ${c==="نشط"||c==="ناجحة"||c==="متوفرة"?"#1a4400":c==="مهتم بعملنا"?"#3a2800":"#330000"}`
    }),
  };

  return (
    <div style={S.app}>
      <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700;900&display=swap" rel="stylesheet"/>
      <header style={S.header}>
        <div>
          <div style={S.logo}>⬡ FERDI COLOUR</div>
          <div style={S.sub}>Sarl Ferdi Colour — ماتيار بروميار</div>
        </div>
        <nav style={S.nav}>
          {pages.map((p,i)=><button key={i} style={S.navBtn(page===i)} onClick={()=>setPage(i)}>{p}</button>)}
        </nav>
      </header>
      <div style={S.body}>
        {page===0 && <PageHome products={products} clients={clients} visits={visits} orders={orders} S={S}/>}
        {page===1 && <PageClients clients={clients} setClients={setClients} visits={visits} setVisits={setVisits} S={S}/>}
        {page===2 && <PageProducts products={products} setProducts={setProducts} orders={orders} S={S}/>}
        {page===3 && <PageVisits visits={visits} setVisits={setVisits} clients={clients} S={S}/>}
        {page===4 && <PageOrders orders={orders} setOrders={setOrders} products={products} clients={clients} S={S}/>}
        {page===5 && <PageBilan clients={clients} visits={visits} orders={orders} expenses={expenses} products={products} S={S}/>}
        {page===6 && <PageExpenses expenses={expenses} setExpenses={setExpenses} clients={clients} S={S}/>}
        {page===7 && <PageGoals goals={goals} setGoals={setGoals} orders={orders} visits={visits} clients={clients} expenses={expenses} S={S}/>}
      </div>
    </div>
  );
}

// ═══════════════════════════════════════════════════════════════
//  PAGE 0 — HOME
// ═══════════════════════════════════════════════════════════════
function PageHome({ products, clients, visits, orders, S }) {
  const totalRevenue = orders.filter(o=>o.confirmed).reduce((s,o)=>s+Number(o.total||0),0);
  const activeClients = clients.filter(c=>c.status==="نشط").length;
  const successVisits = visits.filter(v=>v.success==="ناجحة").length;
  const pendingOrders = orders.filter(o=>!o.confirmed).length;

  return (
    <div>
      <div style={{marginBottom:"24px"}}>
        <h1 style={{fontSize:"28px",fontWeight:"900",color:"#D4A017",margin:0}}>لوحة القيادة</h1>
        <p style={{color:"#666",fontSize:"13px",marginTop:"4px"}}>نظرة شاملة على أداء Sarl Ferdi Colour</p>
      </div>

      <div style={S.grid4}>
        {[
          {label:"إجمالي الإيرادات",val:totalRevenue.toLocaleString()+" دج",icon:"💰"},
          {label:"العملاء النشطون",val:activeClients,icon:"👥"},
          {label:"الزيارات الناجحة",val:successVisits,icon:"✅"},
          {label:"طلبات معلّقة",val:pendingOrders,icon:"⏳"},
        ].map((s,i)=>(
          <div key={i} style={S.stat}>
            <div style={{fontSize:"28px",marginBottom:"8px"}}>{s.icon}</div>
            <div style={S.statNum}>{s.val}</div>
            <div style={S.statLabel}>{s.label}</div>
          </div>
        ))}
      </div>

      <div style={S.cardGold}>
        <div style={S.title}>📦 المنتجات — ماتيار بروميار</div>
        {products.length === 0 ? <p style={{color:"#555",textAlign:"center"}}>لا توجد منتجات مضافة بعد</p> : (
          <table style={S.table}>
            <thead><tr>
              <th style={S.th}>الرمز</th><th style={S.th}>اللون</th>
              <th style={S.th}>سعر البيع / كغ</th><th style={S.th}>الكمية</th>
            </tr></thead>
            <tbody>{products.map((p,i)=>(
              <tr key={i}>
                <td style={S.td}><code style={{color:"#D4A017"}}>{p.code}</code></td>
                <td style={S.td}>{p.color}</td>
                <td style={S.td} style={{...S.td,color:"#D4A017",fontWeight:"bold"}}>{Number(p.price).toLocaleString()} دج</td>
                <td style={S.td}><span style={S.badge(p.stock)}>{p.stock}</span></td>
              </tr>
            ))}</tbody>
          </table>
        )}
      </div>

      <div style={S.grid2}>
        <div style={S.card}>
          <div style={S.title}>📊 آخر الطلبات</div>
          {orders.length===0 ? <p style={{color:"#555"}}>لا توجد طلبات</p> : orders.slice(-5).reverse().map((o,i)=>(
            <div key={i} style={{display:"flex",justifyContent:"space-between",padding:"8px 0",borderBottom:"1px solid #1a1400",fontSize:"13px"}}>
              <span style={{color:"#D4A017"}}>{o.ref}</span>
              <span style={{color:"#ccc"}}>{o.productName}</span>
              <span style={S.badge(o.confirmed?"نشط":"غير نشط")}>{o.confirmed?"مؤكد":"معلّق"}</span>
            </div>
          ))}
        </div>
        <div style={S.card}>
          <div style={S.title}>🗓 آخر الزيارات</div>
          {visits.length===0 ? <p style={{color:"#555"}}>لا توجد زيارات</p> : visits.slice(-5).reverse().map((v,i)=>(
            <div key={i} style={{display:"flex",justifyContent:"space-between",padding:"8px 0",borderBottom:"1px solid #1a1400",fontSize:"13px"}}>
              <span style={{color:"#D4A017"}}>{v.clientId}</span>
              <span style={{color:"#ccc"}}>{v.clientName?.substring(0,20)}</span>
              <span style={S.badge(v.success)}>{v.success}</span>
            </div>
          ))}
        </div>
      </div>
    </div>
  );
}

// ═══════════════════════════════════════════════════════════════
//  PAGE 1 — CLIENTS
// ═══════════════════════════════════════════════════════════════
function PageClients({ clients, setClients, visits, setVisits, S }) {
  const emptyC = { id:"", name:"", wilaya:"", type:"", size:"كبيرة", status:"نشط", firstVisit:"", lastVisit:"", visits:0, notes:"" };
  const emptyR = { clientId:"", clientName:"", phone:"", email:"", date:"", time:"", endTime:"", colorType:"", success:"ناجحة", tradeType:"", supplier:"", brand:"", priorities:[], colorProblems:[], preferredColors:[], quantity:"", opinion:"", suggestions:"", region:"", wilaya:"", notes:"" };
  const [form, setForm] = useState(emptyC);
  const [reg, setReg] = useState(emptyR);
  const [showForm, setShowForm] = useState(false);
  const [showReg, setShowReg] = useState(false);
  const [editId, setEditId] = useState(null);
  const [search, setSearch] = useState("");

  const filtered = clients.filter(c =>
    c.name?.toLowerCase().includes(search.toLowerCase()) ||
    c.id?.toLowerCase().includes(search.toLowerCase()) ||
    c.wilaya?.includes(search)
  );

  const idExists = (id, excludeId=null) => clients.some(c => c.id === id && c.id !== excludeId);

  function saveClient() {
    if (!form.id || !form.name) return alert("يرجى إدخال الرمز والاسم");
    if (editId === null && idExists(form.id)) return alert("رمز العميل موجود مسبقاً");
    if (editId !== null) {
      setClients(clients.map(c => c.id === editId ? { ...form } : c));
      setEditId(null);
    } else {
      setClients([...clients, form]);
    }
    setForm(emptyC); setShowForm(false);
  }

  function deleteClient(id) {
    if (!window.confirm("حذف العميل؟")) return;
    setClients(clients.filter(c => c.id !== id));
  }

  function editClient(c) {
    setForm({ ...c }); setEditId(c.id); setShowForm(true);
  }

  function handleRegClientId(id) {
    const c = clients.find(cl => cl.id === id);
    setReg(r => ({ ...r, clientId: id, clientName: c ? c.name : "", wilaya: c ? c.wilaya : "" }));
  }

  function toggleArr(arr, val) {
    return arr.includes(val) ? arr.filter(x=>x!==val) : [...arr, val];
  }

  function saveVisitReg() {
    if (!reg.clientId || !reg.date) return alert("يرجى تحديد العميل والتاريخ");
    const c = clients.find(cl => cl.id === reg.clientId);
    if (!c) return alert("رمز العميل غير موجود");
    const newV = { ...reg, id: uid("V"), clientName: c.name };
    setVisits(vs => [...vs, newV]);
    setClients(cls => cls.map(cl => cl.id === reg.clientId ? {
      ...cl,
      visits: (Number(cl.visits)||0) + 1,
      lastVisit: reg.date,
      firstVisit: cl.firstVisit || reg.date,
      status: reg.success === "ناجحة" ? "نشط" : cl.status
    } : cl));
    setReg(emptyR); setShowReg(false);
  }

  const clientVisits = (id) => visits.filter(v => v.clientId === id);

  return (
    <div>
      <div style={{display:"flex",justifyContent:"space-between",alignItems:"center",marginBottom:"20px"}}>
        <h1 style={{fontSize:"22px",fontWeight:"900",color:"#D4A017",margin:0}}>👥 إدارة العملاء</h1>
        <div style={{display:"flex",gap:"10px"}}>
          <button style={S.btnGhost} onClick={()=>{setShowReg(!showReg);setShowForm(false)}}>➕ تسجيل زيارة</button>
          <button style={S.btn} onClick={()=>{setShowForm(!showForm);setEditId(null);setForm(emptyC);setShowReg(false)}}>➕ عميل جديد</button>
        </div>
      </div>

      {showForm && (
        <div style={S.cardGold}>
          <div style={S.title}>{editId ? "✏️ تعديل العميل" : "➕ إضافة عميل جديد"}</div>
          <div style={S.grid3}>
            <div><label style={S.label}>رمز العميل (ID) *</label><input style={S.input} value={form.id} onChange={e=>setForm(f=>({...f,id:e.target.value.toUpperCase()}))} placeholder="مثال: CLW01"/></div>
            <div><label style={S.label}>اسم العميل / الشركة *</label><input style={S.input} value={form.name} onChange={e=>setForm(f=>({...f,name:e.target.value}))} placeholder="اسم الزبون أو المؤسسة"/></div>
            <div><label style={S.label}>الولاية</label>
              <select style={S.select} value={form.wilaya} onChange={e=>setForm(f=>({...f,wilaya:e.target.value}))}>
                <option value="">اختر الولاية</option>{WILAYAS.map(w=><option key={w}>{w}</option>)}
              </select>
            </div>
            <div><label style={S.label}>نوع النشاط</label><input style={S.input} value={form.type} onChange={e=>setForm(f=>({...f,type:e.target.value}))} placeholder="نوع التجارة أو الصناعة"/></div>
            <div><label style={S.label}>حجم الشركة</label>
              <select style={S.select} value={form.size} onChange={e=>setForm(f=>({...f,size:e.target.value}))}>
                <option>كبيرة</option><option>صغيرة</option>
              </select>
            </div>
            <div><label style={S.label}>حالة العميل</label>
              <select style={S.select} value={form.status} onChange={e=>setForm(f=>({...f,status:e.target.value}))}>
                {CLIENT_STATUS.map(s=><option key={s}>{s}</option>)}
              </select>
            </div>
            <div><label style={S.label}>أول زيارة</label><input style={S.input} type="date" value={form.firstVisit} onChange={e=>setForm(f=>({...f,firstVisit:e.target.value}))}/></div>
            <div><label style={S.label}>آخر زيارة</label><input style={S.input} type="date" value={form.lastVisit} onChange={e=>setForm(f=>({...f,lastVisit:e.target.value}))}/></div>
            <div><label style={S.label}>ملاحظات</label><input style={S.input} value={form.notes} onChange={e=>setForm(f=>({...f,notes:e.target.value}))}/></div>
          </div>
          <div style={{display:"flex",gap:"10px",marginTop:"16px"}}>
            <button style={S.btn} onClick={saveClient}>{editId?"حفظ التعديل":"إضافة العميل"}</button>
            <button style={S.btnGhost} onClick={()=>{setShowForm(false);setEditId(null);setForm(emptyC)}}>إلغاء</button>
          </div>
        </div>
      )}

      {showReg && (
        <div style={S.cardGold}>
          <div style={S.title}>📋 تسجيل زيارة جديدة</div>
          <div style={S.grid3}>
            <div>
              <label style={S.label}>رمز العميل *</label>
              <input style={S.input} value={reg.clientId} onChange={e=>handleRegClientId(e.target.value.toUpperCase())} placeholder="أدخل رمز العميل"/>
              {reg.clientId && clients.find(c=>c.id===reg.clientId) && <div style={{color:"#44ff88",fontSize:"11px",marginTop:"4px"}}>✓ {clients.find(c=>c.id===reg.clientId).name}</div>}
            </div>
            <div><label style={S.label}>هاتف الشركة</label><input style={S.input} value={reg.phone} onChange={e=>setReg(r=>({...r,phone:e.target.value}))}/></div>
            <div><label style={S.label}>إيميل الشركة</label><input style={S.input} value={reg.email} onChange={e=>setReg(r=>({...r,email:e.target.value}))}/></div>
            <div><label style={S.label}>تاريخ الزيارة *</label><input style={S.input} type="date" value={reg.date} onChange={e=>setReg(r=>({...r,date:e.target.value}))}/></div>
            <div><label style={S.label}>وقت البداية</label><input style={S.input} type="time" value={reg.time} onChange={e=>setReg(r=>({...r,time:e.target.value}))}/></div>
            <div><label style={S.label}>وقت النهاية</label><input style={S.input} type="time" value={reg.endTime} onChange={e=>setReg(r=>({...r,endTime:e.target.value}))}/></div>
            <div><label style={S.label}>نوع الملونات</label>
              <select style={S.select} value={reg.colorType} onChange={e=>setReg(r=>({...r,colorType:e.target.value}))}>
                <option value="">اختر</option>{COLOR_TYPES.map(t=><option key={t}>{t}</option>)}
              </select>
            </div>
            <div><label style={S.label}>نتيجة الزيارة</label>
              <select style={S.select} value={reg.success} onChange={e=>setReg(r=>({...r,success:e.target.value}))}>
                {VISIT_SUCCESS.map(s=><option key={s}>{s}</option>)}
              </select>
            </div>
            <div><label style={S.label}>نوع التجارة / الصناعة</label>
              <select style={S.select} value={reg.tradeType} onChange={e=>setReg(r=>({...r,tradeType:e.target.value}))}>
                <option value="">اختر</option>{TRADE_TYPES.map(t=><option key={t}>{t}</option>)}
              </select>
            </div>
            <div><label style={S.label}>مصدر التمويل / المورد</label>
              <select style={S.select} value={reg.supplier} onChange={e=>setReg(r=>({...r,supplier:e.target.value}))}>
                <option value="">اختر</option>{SUPPLIER_TYPES.map(t=><option key={t}>{t}</option>)}
              </select>
            </div>
            <div><label style={S.label}>اسم العلامة</label><input style={S.input} value={reg.brand} onChange={e=>setReg(r=>({...r,brand:e.target.value}))}/></div>
            <div><label style={S.label}>كمية الاستهلاك المفضلة</label>
              <select style={S.select} value={reg.quantity} onChange={e=>setReg(r=>({...r,quantity:e.target.value}))}>
                <option value="">اختر</option>{QUANTITY_RANGES.map(q=><option key={q}>{q}</option>)}
              </select>
            </div>
            <div><label style={S.label}>رأي الزبون في علامتنا</label>
              <select style={S.select} value={reg.opinion} onChange={e=>setReg(r=>({...r,opinion:e.target.value}))}>
                <option value="">اختر</option>{OPINIONS.map(o=><option key={o}>{o}</option>)}
              </select>
            </div>
            <div><label style={S.label}>المنطقة</label>
              <select style={S.select} value={reg.region} onChange={e=>setReg(r=>({...r,region:e.target.value}))}>
                <option value="">اختر</option>{REGIONS.map(r=><option key={r}>{r}</option>)}
              </select>
            </div>
            <div><label style={S.label}>الولاية</label>
              <select style={S.select} value={reg.wilaya} onChange={e=>setReg(r=>({...r,wilaya:e.target.value}))}>
                <option value="">اختر</option>{WILAYAS.map(w=><option key={w}>{w}</option>)}
              </select>
            </div>
          </div>

          <div style={{marginTop:"12px"}}>
            <label style={S.label}>العوامل التي يهتم بها الزبون</label>
            <div style={{display:"flex",gap:"10px",flexWrap:"wrap",marginTop:"6px"}}>
              {PRIORITIES.map(p=>(
                <label key={p} style={{display:"flex",alignItems:"center",gap:"6px",cursor:"pointer",color:reg.priorities?.includes(p)?"#D4A017":"#888"}}>
                  <input type="checkbox" checked={reg.priorities?.includes(p)||false} onChange={()=>setReg(r=>({...r,priorities:toggleArr(r.priorities||[],p)}))} style={{accentColor:"#D4A017"}}/>
                  {p}
                </label>
              ))}
            </div>
          </div>

          <div style={{marginTop:"12px"}}>
            <label style={S.label}>مشاكل الألوان</label>
            <div style={{display:"flex",gap:"10px",flexWrap:"wrap",marginTop:"6px"}}>
              {PRIORITIES.map(p=>(
                <label key={p} style={{display:"flex",alignItems:"center",gap:"6px",cursor:"pointer",color:reg.colorProblems?.includes(p)?"#D4A017":"#888"}}>
                  <input type="checkbox" checked={reg.colorProblems?.includes(p)||false} onChange={()=>setReg(r=>({...r,colorProblems:toggleArr(r.colorProblems||[],p)}))} style={{accentColor:"#D4A017"}}/>
                  {p}
                </label>
              ))}
            </div>
          </div>

          <div style={{marginTop:"12px"}}>
            <label style={S.label}>الألوان المفضلة</label>
            <div style={{display:"flex",gap:"8px",flexWrap:"wrap",marginTop:"6px"}}>
              {COLORS_LIST.map(c=>(
                <label key={c} style={{display:"flex",alignItems:"center",gap:"4px",cursor:"pointer",padding:"4px 10px",borderRadius:"20px",border:`1px solid ${reg.preferredColors?.includes(c)?"#D4A017":"#2a2200"}`,background:reg.preferredColors?.includes(c)?"#1a1400":"transparent",color:reg.preferredColors?.includes(c)?"#D4A017":"#888",fontSize:"12px",transition:"all 0.15s"}}>
                  <input type="checkbox" checked={reg.preferredColors?.includes(c)||false} onChange={()=>setReg(r=>({...r,preferredColors:toggleArr(r.preferredColors||[],c)}))} style={{display:"none"}}/>
                  {c}
                </label>
              ))}
            </div>
          </div>

          <div style={{marginTop:"12px"}}>
            <label style={S.label}>اقتراحات لتحسين</label>
            <textarea style={{...S.input,minHeight:"60px",resize:"vertical"}} value={reg.suggestions} onChange={e=>setReg(r=>({...r,suggestions:e.target.value}))}/>
          </div>
          <div style={{marginTop:"12px"}}>
            <label style={S.label}>ملاحظات</label>
            <input style={S.input} value={reg.notes} onChange={e=>setReg(r=>({...r,notes:e.target.value}))}/>
          </div>

          <div style={{display:"flex",gap:"10px",marginTop:"16px"}}>
            <button style={S.btn} onClick={saveVisitReg}>حفظ الزيارة</button>
            <button style={S.btnGhost} onClick={()=>setShowReg(false)}>إلغاء</button>
          </div>
        </div>
      )}

      <div style={S.card}>
        <div style={{display:"flex",justifyContent:"space-between",alignItems:"center",marginBottom:"12px"}}>
          <div style={S.title}>قائمة العملاء ({clients.length})</div>
          <input style={{...S.input,maxWidth:"260px"}} placeholder="🔍 بحث بالاسم أو الرمز أو الولاية" value={search} onChange={e=>setSearch(e.target.value)}/>
        </div>
        {filtered.length===0 ? <p style={{color:"#555",textAlign:"center",padding:"20px"}}>لا يوجد عملاء</p> : (
          <div style={{overflowX:"auto"}}>
            <table style={S.table}>
              <thead><tr>
                <th style={S.th}>الرمز</th><th style={S.th}>الاسم</th><th style={S.th}>الولاية</th>
                <th style={S.th}>النشاط</th><th style={S.th}>الحجم</th><th style={S.th}>الحالة</th>
                <th style={S.th}>الزيارات</th><th style={S.th}>آخر زيارة</th><th style={S.th}>إجراءات</th>
              </tr></thead>
              <tbody>{filtered.map((c,i)=>(
                <tr key={i} style={{background: i%2===0?"transparent":"#0d0c0033"}}>
                  <td style={S.td}><code style={{color:"#D4A017",fontWeight:"bold"}}>{c.id}</code></td>
                  <td style={S.td}>{c.name}</td>
                  <td style={S.td}>{c.wilaya}</td>
                  <td style={S.td}>{c.type}</td>
                  <td style={S.td}>{c.size}</td>
                  <td style={S.td}><span style={S.badge(c.status)}>{c.status}</span></td>
                  <td style={S.td}><span style={{color:"#D4A017",fontWeight:"bold"}}>{clientVisits(c.id).length}</span></td>
                  <td style={S.td}>{c.lastVisit||"—"}</td>
                  <td style={S.td}>
                    <div style={{display:"flex",gap:"6px"}}>
                      <button style={S.btnGhost} onClick={()=>editClient(c)}>✏️</button>
                      <button style={S.btnDanger} onClick={()=>deleteClient(c.id)}>🗑</button>
                    </div>
                  </td>
                </tr>
              ))}</tbody>
            </table>
          </div>
        )}
      </div>
    </div>
  );
}

// ═══════════════════════════════════════════════════════════════
//  PAGE 2 — PRODUCTS
// ═══════════════════════════════════════════════════════════════
function PageProducts({ products, setProducts, orders, S }) {
  const empty = { code:"", name:"ماتيار بروميار", color:"", price:"", stock:"متوفرة" };
  const [form, setForm] = useState(empty);
  const [show, setShow] = useState(false);
  const [editCode, setEditCode] = useState(null);

  function save() {
    if (!form.code || !form.color || !form.price) return alert("يرجى ملء جميع الحقول");
    if (editCode === null && products.some(p=>p.code===form.code)) return alert("رمز المنتج موجود مسبقاً");
    if (editCode !== null) {
      setProducts(products.map(p=>p.code===editCode?{...form}:p));
      setEditCode(null);
    } else {
      setProducts([...products, form]);
    }
    setForm(empty); setShow(false);
  }

  function del(code) {
    if (!window.confirm("حذف المنتج؟")) return;
    setProducts(products.filter(p=>p.code!==code));
  }

  // Most sold product chart
  const salesCount = useMemo(() => {
    const map = {};
    orders.forEach(o => { map[o.productCode] = (map[o.productCode]||0) + 1; });
    return map;
  }, [orders]);

  const chartData = products.map(p=>({ label: p.color, value: salesCount[p.code]||0 })).filter(d=>d.value>0);

  return (
    <div>
      <div style={{display:"flex",justifyContent:"space-between",alignItems:"center",marginBottom:"20px"}}>
        <h1 style={{fontSize:"22px",fontWeight:"900",color:"#D4A017",margin:0}}>📦 إدارة المنتجات</h1>
        <button style={S.btn} onClick={()=>{setShow(!show);setEditCode(null);setForm(empty)}}>➕ منتج جديد</button>
      </div>

      {show && (
        <div style={S.cardGold}>
          <div style={S.title}>{editCode?"✏️ تعديل منتج":"➕ إضافة منتج"}</div>
          <div style={S.grid3}>
            <div><label style={S.label}>رمز المنتج *</label><input style={S.input} value={form.code} onChange={e=>setForm(f=>({...f,code:e.target.value.toUpperCase()}))} placeholder="مثال: MAT-BL001"/></div>
            <div><label style={S.label}>اسم المنتج</label><input style={S.input} value={form.name} onChange={e=>setForm(f=>({...f,name:e.target.value}))}/></div>
            <div><label style={S.label}>اللون *</label><input style={S.input} value={form.color} onChange={e=>setForm(f=>({...f,color:e.target.value}))} placeholder="مثال: أبيض"/></div>
            <div><label style={S.label}>سعر البيع / كغ (دج) *</label><input style={S.input} type="number" value={form.price} onChange={e=>setForm(f=>({...f,price:e.target.value}))}/></div>
            <div><label style={S.label}>حالة المخزون</label>
              <select style={S.select} value={form.stock} onChange={e=>setForm(f=>({...f,stock:e.target.value}))}>
                {STOCK_STATUS.map(s=><option key={s}>{s}</option>)}
              </select>
            </div>
          </div>
          <div style={{display:"flex",gap:"10px",marginTop:"16px"}}>
            <button style={S.btn} onClick={save}>{editCode?"حفظ التعديل":"إضافة"}</button>
            <button style={S.btnGhost} onClick={()=>{setShow(false);setEditCode(null);setForm(empty)}}>إلغاء</button>
          </div>
        </div>
      )}

      <div style={S.grid2}>
        <div style={S.card}>
          <div style={S.title}>📦 قائمة المنتجات ({products.length})</div>
          {products.length===0 ? <p style={{color:"#555",textAlign:"center",padding:"20px"}}>لا توجد منتجات</p> : (
            <table style={S.table}>
              <thead><tr>
                <th style={S.th}>الرمز</th><th style={S.th}>اللون</th>
                <th style={S.th}>السعر/كغ</th><th style={S.th}>الكمية</th><th style={S.th}>إجراءات</th>
              </tr></thead>
              <tbody>{products.map((p,i)=>(
                <tr key={i}>
                  <td style={S.td}><code style={{color:"#D4A017"}}>{p.code}</code></td>
                  <td style={S.td}>{p.color}</td>
                  <td style={{...S.td,color:"#D4A017",fontWeight:"bold"}}>{Number(p.price).toLocaleString()} دج</td>
                  <td style={S.td}><span style={S.badge(p.stock)}>{p.stock}</span></td>
                  <td style={S.td}>
                    <div style={{display:"flex",gap:"6px"}}>
                      <button style={S.btnGhost} onClick={()=>{setForm({...p});setEditCode(p.code);setShow(true)}}>✏️</button>
                      <button style={S.btnDanger} onClick={()=>del(p.code)}>🗑</button>
                    </div>
                  </td>
                </tr>
              ))}</tbody>
            </table>
          )}
        </div>
        <div style={S.card}>
          <div style={S.title}>📊 أكثر المنتجات مبيعاً</div>
          {chartData.length===0 ? <p style={{color:"#555",textAlign:"center",padding:"20px"}}>لا توجد بيانات مبيعات بعد</p> : <PieChart data={chartData}/>}
        </div>
      </div>
    </div>
  );
}

// ═══════════════════════════════════════════════════════════════
//  PAGE 3 — VISITS
// ═══════════════════════════════════════════════════════════════
function PageVisits({ visits, setVisits, clients, S }) {
  function del(id) {
    if (!window.confirm("حذف الزيارة؟")) return;
    setVisits(visits.filter(v=>v.id!==id));
  }

  const successData = [
    { label:"ناجحة", value: visits.filter(v=>v.success==="ناجحة").length },
    { label:"غير ناجحة", value: visits.filter(v=>v.success==="غير ناجحة").length },
    { label:"مهتم بعملنا", value: visits.filter(v=>v.success==="مهتم بعملنا").length },
  ].filter(d=>d.value>0);

  // Most visited client by minutes
  const visitDurations = useMemo(() => {
    const map = {};
    visits.forEach(v => {
      if (!v.time || !v.endTime) return;
      const [h1,m1] = v.time.split(":").map(Number);
      const [h2,m2] = v.endTime.split(":").map(Number);
      const diff = (h2*60+m2) - (h1*60+m1);
      if (diff>0) map[v.clientId] = (map[v.clientId]||0) + diff;
    });
    return Object.entries(map).sort((a,b)=>b[1]-a[1]).slice(0,5);
  }, [visits]);

  const sortedVisits = [...visits].sort((a,b)=>new Date(b.date)-new Date(a.date));

  return (
    <div>
      <h1 style={{fontSize:"22px",fontWeight:"900",color:"#D4A017",marginBottom:"20px"}}>🗓 سجل الزيارات</h1>

      <div style={S.grid2}>
        <div style={S.card}>
          <div style={S.title}>📊 بيلان الزيارات</div>
          <PieChart data={successData}/>
          <div style={{marginTop:"16px",display:"flex",gap:"12px",flexWrap:"wrap"}}>
            <div style={S.stat}><div style={S.statNum}>{visits.length}</div><div style={S.statLabel}>إجمالي الزيارات</div></div>
            <div style={S.stat}><div style={S.statNum}>{visits.filter(v=>v.success==="ناجحة").length}</div><div style={S.statLabel}>ناجحة</div></div>
            <div style={S.stat}><div style={S.statNum}>{visits.filter(v=>v.success==="غير ناجحة").length}</div><div style={S.statLabel}>غير ناجحة</div></div>
          </div>
        </div>
        <div style={S.card}>
          <div style={S.title}>⏱ أكثر عميل تمت زيارته (بالدقائق)</div>
          {visitDurations.length===0 ? <p style={{color:"#555"}}>لا توجد بيانات وقت</p> : (
            <div style={{display:"flex",flexDirection:"column",gap:"10px"}}>
              {visitDurations.map(([id,mins],i)=>{
                const c = clients.find(cl=>cl.id===id);
                return (
                  <div key={i} style={{display:"flex",alignItems:"center",gap:"10px"}}>
                    <span style={{color:"#D4A017",fontWeight:"bold",minWidth:"50px"}}>{id}</span>
                    <span style={{color:"#ccc",fontSize:"13px",flex:1}}>{c?.name||"—"}</span>
                    <div style={{background:"#1a1400",borderRadius:"4px",height:"12px",flex:2,position:"relative"}}>
                      <div style={{background:"linear-gradient(90deg,#D4A017,#A07810)",height:"100%",borderRadius:"4px",width:`${Math.min(100,(mins/visitDurations[0][1])*100)}%`}}/>
                    </div>
                    <span style={{color:"#D4A017",fontSize:"12px",minWidth:"60px"}}>{mins} دقيقة</span>
                  </div>
                );
              })}
            </div>
          )}
        </div>
      </div>

      <div style={S.card}>
        <div style={S.title}>📋 جدول الزيارات ({visits.length})</div>
        {sortedVisits.length===0 ? <p style={{color:"#555",textAlign:"center",padding:"20px"}}>لا توجد زيارات مسجلة — أضف زيارة من صفحة العملاء</p> : (
          <div style={{overflowX:"auto"}}>
            <table style={S.table}>
              <thead><tr>
                <th style={S.th}>ID</th><th style={S.th}>العميل</th><th style={S.th}>التاريخ</th>
                <th style={S.th}>البداية</th><th style={S.th}>النهاية</th>
                <th style={S.th}>الملونات</th><th style={S.th}>النتيجة</th>
                <th style={S.th}>الكمية</th><th style={S.th}>حذف</th>
              </tr></thead>
              <tbody>{sortedVisits.map((v,i)=>(
                <tr key={i} style={{background:i%2===0?"transparent":"#0d0c0033"}}>
                  <td style={S.td}><code style={{color:"#D4A017"}}>{v.clientId}</code></td>
                  <td style={S.td}>{v.clientName}</td>
                  <td style={S.td}>{v.date}</td>
                  <td style={S.td}>{v.time||"—"}</td>
                  <td style={S.td}>{v.endTime||"—"}</td>
                  <td style={S.td}>{v.colorType}</td>
                  <td style={S.td}><span style={S.badge(v.success)}>{v.success}</span></td>
                  <td style={S.td}><span style={{fontSize:"11px",color:"#aaa"}}>{v.quantity}</span></td>
                  <td style={S.td}><button style={S.btnDanger} onClick={()=>del(v.id)}>🗑</button></td>
                </tr>
              ))}</tbody>
            </table>
          </div>
        )}
      </div>
    </div>
  );
}

// ═══════════════════════════════════════════════════════════════
//  PAGE 4 — ORDERS
// ═══════════════════════════════════════════════════════════════
function PageOrders({ orders, setOrders, products, clients, S }) {
  const empty = { productCode:"", productName:"", clientId:"", price:"", qty:"", total:"", confirmed:false, date: new Date().toISOString().split("T")[0] };
  const [form, setForm] = useState(empty);
  const [show, setShow] = useState(false);

  function nextRef() {
    const year = new Date().getFullYear();
    if (orders.length===0) return `BCH01/${year}`;
    const nums = orders.map(o=>{
      const m = o.ref?.match(/BCH(\d+)\//);
      return m ? parseInt(m[1]) : 0;
    });
    const next = Math.max(...nums) + 1;
    return `BCH${String(next).padStart(2,"0")}/${year}`;
  }

  function handleProduct(code) {
    const p = products.find(pr=>pr.code===code);
    setForm(f=>({...f,productCode:code,productName:p?p.name:"",price:p?p.price:""}));
  }

  function handleClient(id) {
    const c = clients.find(cl=>cl.id===id);
    setForm(f=>({...f,clientId:id,clientName:c?c.name:""}));
  }

  function calcTotal(qty,price) {
    const t = (Number(qty)||0)*(Number(price)||0);
    setForm(f=>({...f,qty,total:t}));
  }

  function save() {
    if (!form.productCode || !form.qty) return alert("يرجى تحديد المنتج والكمية");
    setOrders(os=>[...os,{...form,ref:nextRef()}]);
    setForm(empty); setShow(false);
  }

  function toggle(ref) {
    setOrders(os=>os.map(o=>o.ref===ref?{...o,confirmed:!o.confirmed}:o));
  }

  function del(ref) {
    if (!window.confirm("حذف الطلب؟")) return;
    setOrders(os=>os.filter(o=>o.ref!==ref));
  }

  const confirmed = orders.filter(o=>o.confirmed);
  const revenue = confirmed.reduce((s,o)=>s+Number(o.total||0),0);

  return (
    <div>
      <div style={{display:"flex",justifyContent:"space-between",alignItems:"center",marginBottom:"20px"}}>
        <h1 style={{fontSize:"22px",fontWeight:"900",color:"#D4A017",margin:0}}>📋 إدارة الطلبات</h1>
        <button style={S.btn} onClick={()=>setShow(!show)}>➕ طلب جديد</button>
      </div>

      <div style={S.grid4}>
        <div style={S.stat}><div style={S.statNum}>{orders.length}</div><div style={S.statLabel}>إجمالي الطلبات</div></div>
        <div style={S.stat}><div style={S.statNum}>{confirmed.length}</div><div style={S.statLabel}>طلبات مؤكدة</div></div>
        <div style={S.stat}><div style={S.statNum}>{orders.length-confirmed.length}</div><div style={S.statLabel}>طلبات معلّقة</div></div>
        <div style={S.stat}><div style={S.statNum}>{revenue.toLocaleString()}</div><div style={S.statLabel}>الإيرادات (دج)</div></div>
      </div>

      {show && (
        <div style={S.cardGold}>
          <div style={S.title}>➕ طلب جديد — <span style={{color:"#888",fontSize:"14px"}}>{nextRef()}</span></div>
          <div style={S.grid3}>
            <div>
              <label style={S.label}>رمز المنتج *</label>
              <select style={S.select} value={form.productCode} onChange={e=>handleProduct(e.target.value)}>
                <option value="">اختر المنتج</option>
                {products.map(p=><option key={p.code} value={p.code}>{p.code} — {p.color}</option>)}
              </select>
            </div>
            <div>
              <label style={S.label}>رمز العميل</label>
              <select style={S.select} value={form.clientId} onChange={e=>handleClient(e.target.value)}>
                <option value="">اختر العميل (اختياري)</option>
                {clients.map(c=><option key={c.id} value={c.id}>{c.id} — {c.name}</option>)}
              </select>
            </div>
            <div><label style={S.label}>التاريخ</label><input style={S.input} type="date" value={form.date} onChange={e=>setForm(f=>({...f,date:e.target.value}))}/></div>
            <div>
              <label style={S.label}>سعر البيع / كغ (دج)</label>
              <input style={S.input} type="number" value={form.price} onChange={e=>{setForm(f=>({...f,price:e.target.value,total:(Number(f.qty)||0)*Number(e.target.value)}))}}/>
            </div>
            <div>
              <label style={S.label}>الكمية (كغ) *</label>
              <input style={S.input} type="number" value={form.qty} onChange={e=>calcTotal(e.target.value,form.price)}/>
            </div>
            <div>
              <label style={S.label}>السعر الإجمالي (دج)</label>
              <input style={{...S.input,color:"#D4A017",fontWeight:"bold"}} value={Number(form.total).toLocaleString()} readOnly/>
            </div>
          </div>
          <div style={{display:"flex",gap:"10px",marginTop:"16px"}}>
            <button style={S.btn} onClick={save}>تسجيل الطلب</button>
            <button style={S.btnGhost} onClick={()=>setShow(false)}>إلغاء</button>
          </div>
        </div>
      )}

      <div style={S.card}>
        <div style={S.title}>📋 جدول الطلبات</div>
        {orders.length===0 ? <p style={{color:"#555",textAlign:"center",padding:"20px"}}>لا توجد طلبات</p> : (
          <div style={{overflowX:"auto"}}>
            <table style={S.table}>
              <thead><tr>
                <th style={S.th}>المرجع</th><th style={S.th}>التاريخ</th><th style={S.th}>العميل</th>
                <th style={S.th}>المنتج</th><th style={S.th}>الكمية</th>
                <th style={S.th}>السعر/كغ</th><th style={S.th}>الإجمالي</th>
                <th style={S.th}>الحالة</th><th style={S.th}>إجراءات</th>
              </tr></thead>
              <tbody>{[...orders].reverse().map((o,i)=>(
                <tr key={i} style={{background:i%2===0?"transparent":"#0d0c0033"}}>
                  <td style={S.td}><code style={{color:"#D4A017",fontWeight:"bold"}}>{o.ref}</code></td>
                  <td style={S.td}>{o.date}</td>
                  <td style={S.td}>{o.clientId||"—"}</td>
                  <td style={S.td}>{o.productCode}</td>
                  <td style={S.td}>{Number(o.qty).toLocaleString()} كغ</td>
                  <td style={S.td}>{Number(o.price).toLocaleString()} دج</td>
                  <td style={{...S.td,color:"#D4A017",fontWeight:"bold"}}>{Number(o.total).toLocaleString()} دج</td>
                  <td style={S.td}><span style={S.badge(o.confirmed?"نشط":"غير نشط")}>{o.confirmed?"مؤكد":"معلّق"}</span></td>
                  <td style={S.td}>
                    <div style={{display:"flex",gap:"6px"}}>
                      <button style={S.btnGhost} onClick={()=>toggle(o.ref)}>{o.confirmed?"إلغاء":"تأكيد"}</button>
                      <button style={S.btnDanger} onClick={()=>del(o.ref)}>🗑</button>
                    </div>
                  </td>
                </tr>
              ))}</tbody>
            </table>
          </div>
        )}
      </div>
    </div>
  );
}

// ═══════════════════════════════════════════════════════════════
//  PAGE 5 — BILAN GLOBAL
// ═══════════════════════════════════════════════════════════════
function PageBilan({ clients, visits, orders, expenses, products, S }) {
  const confirmed = orders.filter(o=>o.confirmed);
  const revenue = confirmed.reduce((s,o)=>s+Number(o.total||0),0);
  const totalExpenses = expenses.reduce((s,e)=>s+Number(e.amount||0),0);
  const successVisits = visits.filter(v=>v.success==="ناجحة").length;
  const successRate = visits.length ? Math.round((successVisits/visits.length)*100) : 0;
  const activeClients = clients.filter(c=>c.status==="نشط").length;
  const netProfit = revenue - totalExpenses;

  const visitsByResult = [
    {label:"ناجحة",value:visits.filter(v=>v.success==="ناجحة").length},
    {label:"غير ناجحة",value:visits.filter(v=>v.success==="غير ناجحة").length},
    {label:"مهتم",value:visits.filter(v=>v.success==="مهتم بعملنا").length},
  ].filter(d=>d.value>0);

  const expensesByType = EXPENSE_TYPES.map(t=>({
    label:t, value: expenses.filter(e=>e.type===t).reduce((s,e)=>s+Number(e.amount||0),0)
  })).filter(d=>d.value>0);

  const now = new Date();
  const month = now.toLocaleString("ar",{month:"long",year:"numeric"});

  return (
    <div>
      <div style={{...S.cardGold,background:"linear-gradient(135deg,#1a1200,#0d0900)",border:"1px solid #D4A01766",textAlign:"center",padding:"32px"}}>
        <div style={{fontSize:"13px",color:"#888",letterSpacing:"4px",textTransform:"uppercase",marginBottom:"8px"}}>SARL FERDI COLOUR</div>
        <h1 style={{fontSize:"32px",fontWeight:"900",color:"#D4A017",margin:"0 0 4px"}}>البيلان الشامل</h1>
        <div style={{color:"#888",fontSize:"14px"}}>{month} — ماتيار بروميار</div>
      </div>

      <div style={S.grid4}>
        {[
          {label:"إجمالي الإيرادات",val:revenue.toLocaleString()+" دج",icon:"💰"},
          {label:"صافي الربح",val:netProfit.toLocaleString()+" دج",icon:"📈"},
          {label:"إجمالي المصاريف",val:totalExpenses.toLocaleString()+" دج",icon:"💸"},
          {label:"الطلبات المؤكدة",val:confirmed.length,icon:"✅"},
        ].map((s,i)=>(
          <div key={i} style={{...S.stat,border:i===0?"1px solid #D4A01744":"1px solid #2a2200"}}>
            <div style={{fontSize:"24px",marginBottom:"6px"}}>{s.icon}</div>
            <div style={{...S.statNum,fontSize:i===0?"22px":"24px"}}>{s.val}</div>
            <div style={S.statLabel}>{s.label}</div>
          </div>
        ))}
      </div>

      <div style={S.grid2}>
        <div style={S.card}>
          <div style={S.title}>👥 بيلان العملاء</div>
          <div style={{display:"flex",flexDirection:"column",gap:"10px"}}>
            {[
              ["إجمالي العملاء",clients.length],
              ["عملاء نشطون",activeClients],
              ["عملاء غير نشطين",clients.filter(c=>c.status==="غير نشط").length],
              ["مهتمون بعملنا",clients.filter(c=>c.status==="مهتم بعملنا").length],
            ].map(([l,v],i)=>(
              <div key={i} style={{display:"flex",justifyContent:"space-between",padding:"8px 12px",background:"#0d0c00",borderRadius:"8px"}}>
                <span style={{color:"#aaa"}}>{l}</span>
                <span style={{color:"#D4A017",fontWeight:"bold"}}>{v}</span>
              </div>
            ))}
          </div>
        </div>
        <div style={S.card}>
          <div style={S.title}>🗓 بيلان الزيارات</div>
          <div style={{marginBottom:"16px"}}><PieChart data={visitsByResult} size={130}/></div>
          {[
            ["معدل النجاح",successRate+"%"],
            ["إجمالي الزيارات",visits.length],
          ].map(([l,v],i)=>(
            <div key={i} style={{display:"flex",justifyContent:"space-between",padding:"8px 12px",background:"#0d0c00",borderRadius:"8px",marginTop:"6px"}}>
              <span style={{color:"#aaa"}}>{l}</span>
              <span style={{color:"#D4A017",fontWeight:"bold"}}>{v}</span>
            </div>
          ))}
        </div>
      </div>

      <div style={S.grid2}>
        <div style={S.card}>
          <div style={S.title}>📦 بيلان المنتجات</div>
          {[
            ["إجمالي المنتجات",products.length],
            ["متوفرة",products.filter(p=>p.stock==="متوفرة").length],
            ["غير متوفرة",products.filter(p=>p.stock==="غير متوفرة").length],
            ["في تصنيع",products.filter(p=>p.stock==="في تصنيع").length],
          ].map(([l,v],i)=>(
            <div key={i} style={{display:"flex",justifyContent:"space-between",padding:"8px 12px",background:"#0d0c00",borderRadius:"8px",marginTop:"6px"}}>
              <span style={{color:"#aaa"}}>{l}</span>
              <span style={{color:"#D4A017",fontWeight:"bold"}}>{v}</span>
            </div>
          ))}
        </div>
        <div style={S.card}>
          <div style={S.title}>💸 بيلان المصاريف</div>
          {expensesByType.length===0 ? <p style={{color:"#555"}}>لا توجد مصاريف</p> : <PieChart data={expensesByType} size={130}/>}
          <div style={{display:"flex",justifyContent:"space-between",padding:"10px 12px",background:"#1a1000",borderRadius:"8px",marginTop:"10px",border:"1px solid #D4A01733"}}>
            <span style={{color:"#D4A017",fontWeight:"bold"}}>الإجمالي</span>
            <span style={{color:"#D4A017",fontWeight:"900"}}>{totalExpenses.toLocaleString()} دج</span>
          </div>
        </div>
      </div>

      <div style={{...S.cardGold,textAlign:"center"}}>
        <div style={{fontSize:"14px",color:"#888",marginBottom:"8px"}}>التقييم الإجمالي للأداء</div>
        <div style={{fontSize:"48px",fontWeight:"900",color: confirmed.length<10?"#ff4444":confirmed.length<30?"#D4A017":"#44ff88"}}>
          {confirmed.length<10?"ضعيف":confirmed.length<30?"جيد":"ممتاز"}
        </div>
        <div style={{fontSize:"14px",color:"#888",marginTop:"4px"}}>
          {confirmed.length} طلب مؤكد — {confirmed.length<10?"أقل من 10 طلبات":confirmed.length<30?"بين 10 و30 طلب":"أكثر من 30 طلب"}
        </div>
        <div style={{marginTop:"16px",background:"#0d0c00",borderRadius:"12px",height:"12px",overflow:"hidden"}}>
          <div style={{background:"linear-gradient(90deg,#D4A017,#44ff88)",height:"100%",width:`${Math.min(100,(confirmed.length/30)*100)}%`,transition:"width 1s ease",borderRadius:"12px"}}/>
        </div>
        <div style={{marginTop:"6px",fontSize:"12px",color:"#666"}}>{Math.round(Math.min(100,(confirmed.length/30)*100))}% من الهدف الأساسي</div>
      </div>
    </div>
  );
}

// ═══════════════════════════════════════════════════════════════
//  PAGE 6 — EXPENSES
// ═══════════════════════════════════════════════════════════════
function PageExpenses({ expenses, setExpenses, clients, S }) {
  const empty = { clientId:"", type:"تنقل", amount:"", date:new Date().toISOString().split("T")[0], notes:"" };
  const [form, setForm] = useState(empty);
  const [show, setShow] = useState(false);

  function handleClientId(id) {
    const c = clients.find(cl=>cl.id===id);
    setForm(f=>({...f,clientId:id,clientName:c?c.name:""}));
  }

  function save() {
    if (!form.amount) return alert("يرجى إدخال المبلغ");
    setExpenses(es=>[...es,{...form,id:uid("EX")}]);
    setForm(empty); setShow(false);
  }

  function del(id) {
    if (!window.confirm("حذف المصروف؟")) return;
    setExpenses(es=>es.filter(e=>e.id!==id));
  }

  const total = expenses.reduce((s,e)=>s+Number(e.amount||0),0);
  const byType = EXPENSE_TYPES.map(t=>({label:t,value:expenses.filter(e=>e.type===t).reduce((s,e)=>s+Number(e.amount||0),0)})).filter(d=>d.value>0);

  return (
    <div>
      <div style={{display:"flex",justifyContent:"space-between",alignItems:"center",marginBottom:"20px"}}>
        <h1 style={{fontSize:"22px",fontWeight:"900",color:"#D4A017",margin:0}}>💸 إدارة المصاريف</h1>
        <button style={S.btn} onClick={()=>setShow(!show)}>➕ مصروف جديد</button>
      </div>

      {show && (
        <div style={S.cardGold}>
          <div style={S.title}>➕ تسجيل مصروف</div>
          <div style={S.grid3}>
            <div>
              <label style={S.label}>رمز العميل (اختياري)</label>
              <input style={S.input} value={form.clientId} onChange={e=>handleClientId(e.target.value.toUpperCase())} placeholder="مثال: CLW01"/>
              {form.clientId && clients.find(c=>c.id===form.clientId) && <div style={{color:"#44ff88",fontSize:"11px",marginTop:"4px"}}>✓ {clients.find(c=>c.id===form.clientId).name}</div>}
            </div>
            <div><label style={S.label}>نوع المصروف</label>
              <select style={S.select} value={form.type} onChange={e=>setForm(f=>({...f,type:e.target.value}))}>
                {EXPENSE_TYPES.map(t=><option key={t}>{t}</option>)}
              </select>
            </div>
            <div><label style={S.label}>المبلغ (دج) *</label><input style={S.input} type="number" value={form.amount} onChange={e=>setForm(f=>({...f,amount:e.target.value}))}/></div>
            <div><label style={S.label}>التاريخ</label><input style={S.input} type="date" value={form.date} onChange={e=>setForm(f=>({...f,date:e.target.value}))}/></div>
            <div><label style={S.label}>ملاحظات</label><input style={S.input} value={form.notes} onChange={e=>setForm(f=>({...f,notes:e.target.value}))}/></div>
          </div>
          <div style={{display:"flex",gap:"10px",marginTop:"16px"}}>
            <button style={S.btn} onClick={save}>حفظ</button>
            <button style={S.btnGhost} onClick={()=>setShow(false)}>إلغاء</button>
          </div>
        </div>
      )}

      <div style={S.grid2}>
        <div style={S.card}>
          <div style={S.title}>📊 المصاريف حسب النوع</div>
          {byType.length===0 ? <p style={{color:"#555"}}>لا توجد مصاريف</p> : <PieChart data={byType}/>}
          <div style={{display:"flex",justifyContent:"space-between",padding:"12px",background:"#1a1000",borderRadius:"10px",marginTop:"12px",border:"1px solid #D4A01733"}}>
            <span style={{color:"#D4A017",fontWeight:"bold"}}>الإجمالي</span>
            <span style={{color:"#D4A017",fontWeight:"900",fontSize:"18px"}}>{total.toLocaleString()} دج</span>
          </div>
        </div>
        <div style={S.card}>
          <div style={S.title}>📋 آخر المصاريف</div>
          {expenses.length===0 ? <p style={{color:"#555"}}>لا توجد مصاريف</p> : (
            <div style={{display:"flex",flexDirection:"column",gap:"6px",maxHeight:"300px",overflowY:"auto"}}>
              {[...expenses].reverse().map((e,i)=>(
                <div key={i} style={{display:"flex",justifyContent:"space-between",alignItems:"center",padding:"8px 12px",background:"#0d0c00",borderRadius:"8px"}}>
                  <div>
                    <div style={{color:"#ccc",fontSize:"13px"}}>{e.type}</div>
                    <div style={{color:"#666",fontSize:"11px"}}>{e.date} {e.clientId?`— ${e.clientId}`:""}</div>
                  </div>
                  <div style={{display:"flex",alignItems:"center",gap:"10px"}}>
                    <span style={{color:"#D4A017",fontWeight:"bold"}}>{Number(e.amount).toLocaleString()} دج</span>
                    <button style={S.btnDanger} onClick={()=>del(e.id)}>🗑</button>
                  </div>
                </div>
              ))}
            </div>
          )}
        </div>
      </div>

      <div style={S.card}>
        <div style={S.title}>📋 جدول المصاريف</div>
        {expenses.length===0 ? <p style={{color:"#555",textAlign:"center",padding:"20px"}}>لا توجد مصاريف</p> : (
          <table style={S.table}>
            <thead><tr>
              <th style={S.th}>التاريخ</th><th style={S.th}>العميل</th>
              <th style={S.th}>النوع</th><th style={S.th}>المبلغ</th>
              <th style={S.th}>ملاحظات</th><th style={S.th}>حذف</th>
            </tr></thead>
            <tbody>{[...expenses].reverse().map((e,i)=>(
              <tr key={i}>
                <td style={S.td}>{e.date}</td>
                <td style={S.td}>{e.clientId||"—"}</td>
                <td style={S.td}>{e.type}</td>
                <td style={{...S.td,color:"#D4A017",fontWeight:"bold"}}>{Number(e.amount).toLocaleString()} دج</td>
                <td style={S.td}>{e.notes||"—"}</td>
                <td style={S.td}><button style={S.btnDanger} onClick={()=>del(e.id)}>🗑</button></td>
              </tr>
            ))}</tbody>
          </table>
        )}
      </div>
    </div>
  );
}

// ═══════════════════════════════════════════════════════════════
//  PAGE 7 — GOALS / PERFORMANCE
// ═══════════════════════════════════════════════════════════════
function PageGoals({ goals, setGoals, orders, visits, clients, expenses, S }) {
  const [edit, setEdit] = useState(false);
  const [form, setForm] = useState(goals);

  useEffect(()=>setForm(goals),[goals]);

  const confirmed = orders.filter(o=>o.confirmed);
  const revenue = confirmed.reduce((s,o)=>s+Number(o.total||0),0);
  const successV = visits.filter(v=>v.success==="ناجحة").length;
  const newC = clients.length;
  const totalExp = expenses.reduce((s,e)=>s+Number(e.amount||0),0);

  const metrics = [
    { label:"الطلبات المؤكدة", current: confirmed.length, target: goals.monthly, unit:"طلب", icon:"📋" },
    { label:"الإيرادات", current: revenue, target: goals.revenue, unit:"دج", icon:"💰" },
    { label:"الزيارات الناجحة", current: successV, target: goals.visitTarget, unit:"زيارة", icon:"✅" },
    { label:"عدد العملاء", current: newC, target: goals.newClients, unit:"عميل", icon:"👥" },
  ];

  function pct(c,t) { return t?Math.min(100,Math.round((c/t)*100)):0; }

  function getColor(p) {
    if(p>=80) return "#44ff88";
    if(p>=50) return "#D4A017";
    return "#ff4444";
  }

  function saveGoals() {
    setGoals(form);
    setEdit(false);
  }

  return (
    <div>
      <div style={{display:"flex",justifyContent:"space-between",alignItems:"center",marginBottom:"20px"}}>
        <h1 style={{fontSize:"22px",fontWeight:"900",color:"#D4A017",margin:0}}>🎯 الأهداف والأداء</h1>
        <button style={S.btnGhost} onClick={()=>setEdit(!edit)}>{edit?"إلغاء":"✏️ تعديل الأهداف"}</button>
      </div>

      {edit && (
        <div style={S.cardGold}>
          <div style={S.title}>🎯 تحديد الأهداف</div>
          <div style={S.grid3}>
            <div><label style={S.label}>هدف الطلبات الشهرية</label><input style={S.input} type="number" value={form.monthly} onChange={e=>setForm(f=>({...f,monthly:Number(e.target.value)}))}/></div>
            <div><label style={S.label}>هدف الإيرادات (دج)</label><input style={S.input} type="number" value={form.revenue} onChange={e=>setForm(f=>({...f,revenue:Number(e.target.value)}))}/></div>
            <div><label style={S.label}>هدف الزيارات الناجحة</label><input style={S.input} type="number" value={form.visitTarget} onChange={e=>setForm(f=>({...f,visitTarget:Number(e.target.value)}))}/></div>
            <div><label style={S.label}>هدف عدد العملاء</label><input style={S.input} type="number" value={form.newClients} onChange={e=>setForm(f=>({...f,newClients:Number(e.target.value)}))}/></div>
            <div><label style={S.label}>معدل النجاح المستهدف (%)</label><input style={S.input} type="number" value={form.successRate} onChange={e=>setForm(f=>({...f,successRate:Number(e.target.value)}))}/></div>
            <div><label style={S.label}>ملاحظة شخصية</label><input style={S.input} value={form.note} onChange={e=>setForm(f=>({...f,note:e.target.value}))} placeholder="رسالتك لنفسك..."/></div>
          </div>
          <div style={{display:"flex",gap:"10px",marginTop:"16px"}}>
            <button style={S.btn} onClick={saveGoals}>حفظ الأهداف</button>
            <button style={S.btnGhost} onClick={()=>setEdit(false)}>إلغاء</button>
          </div>
        </div>
      )}

      {goals.note && (
        <div style={{...S.cardGold,textAlign:"center",padding:"20px",fontStyle:"italic",fontSize:"16px",color:"#D4A017",borderColor:"#D4A01766"}}>
          ✨ {goals.note}
        </div>
      )}

      <div style={{display:"grid",gridTemplateColumns:"1fr 1fr",gap:"16px",marginBottom:"20px"}}>
        {metrics.map((m,i)=>{
          const p = pct(m.current,m.target);
          return (
            <div key={i} style={{...S.card,position:"relative",overflow:"hidden"}}>
              <div style={{display:"flex",justifyContent:"space-between",alignItems:"flex-start",marginBottom:"16px"}}>
                <div>
                  <div style={{fontSize:"24px",marginBottom:"4px"}}>{m.icon}</div>
                  <div style={{color:"#888",fontSize:"12px"}}>{m.label}</div>
                </div>
                <div style={{textAlign:"left"}}>
                  <div style={{fontSize:"28px",fontWeight:"900",color:getColor(p)}}>{p}%</div>
                  <div style={{fontSize:"11px",color:"#666"}}>{m.current.toLocaleString()} / {m.target.toLocaleString()} {m.unit}</div>
                </div>
              </div>
              <div style={{background:"#0d0c00",borderRadius:"6px",height:"8px",overflow:"hidden"}}>
                <div style={{background:`linear-gradient(90deg,${getColor(p)}88,${getColor(p)})`,height:"100%",width:`${p}%`,transition:"width 1s",borderRadius:"6px"}}/>
              </div>
              <div style={{fontSize:"11px",color:"#555",marginTop:"6px"}}>
                {p>=100?"🏆 تم تحقيق الهدف!":p>=80?"💪 أنت قريب من الهدف":p>=50?"📈 في الطريق الصحيح":"⚠️ يحتاج جهد إضافي"}
              </div>
            </div>
          );
        })}
      </div>

      <div style={S.card}>
        <div style={S.title}>📊 ملخص الأداء الشهري</div>
        <div style={{display:"grid",gridTemplateColumns:"repeat(3,1fr)",gap:"12px"}}>
          {[
            {l:"نسبة تحقيق الطلبات",v:pct(confirmed.length,goals.monthly)+"%"},
            {l:"نسبة تحقيق الإيرادات",v:pct(revenue,goals.revenue)+"%"},
            {l:"معدل نجاح الزيارات",v:(visits.length?Math.round((successV/visits.length)*100):0)+"%"},
            {l:"إجمالي المصاريف",v:totalExp.toLocaleString()+" دج"},
            {l:"صافي الإيرادات",v:(revenue-totalExp).toLocaleString()+" دج"},
            {l:"عدد العملاء",v:clients.length},
          ].map((s,i)=>(
            <div key={i} style={{background:"#0d0c00",borderRadius:"10px",padding:"16px",textAlign:"center"}}>
              <div style={{color:"#D4A017",fontWeight:"900",fontSize:"20px"}}>{s.v}</div>
              <div style={{color:"#666",fontSize:"11px",marginTop:"4px"}}>{s.l}</div>
            </div>
          ))}
        </div>
      </div>
    </div>
  );
}
