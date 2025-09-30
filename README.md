<!doctype html>
<div class="modal-card">
<button class="close" id="closeModal">Cerrar ✕</button>
<img id="modalImg" src="" alt="Detalle bicicleta">
<div style="margin-top:10px;display:flex;justify-content:space-between;align-items:center">
<div>
<h3 id="modalTitle">Título bicicleta</h3>
<p id="modalDesc" style="color:var(--muted)">Descripción</p>
</div>
<a id="modalAction" class="btn" href="#">Ver más</a>
</div>
</div>
</div>


<script>
const bikes = [
{title:'Clásica Romántica',desc:'Un paseo al atardecer contigo es el paraíso.',img:'https://images.unsplash.com/photo-1509395176047-4a66953fd231?auto=format&fit=crop&w=800&q=60'},
{title:'Speed Amore',desc:'A tu lado, las rutas largas parecen cortas.',img:'https://images.unsplash.com/photo-1520975910394-7a0a3d1c0c03?auto=format&fit=crop&w=800&q=60'},
{title:'Urbana Cómplíce',desc:'Para llevar flores, cartas y todo mi amor.',img:'https://images.unsplash.com/photo-1444667487784-1b0bf5c5d6f4?auto=format&fit=crop&w=800&q=60'},
{title:'Montaña Corazón',desc:'Juntos conquistamos cualquier camino difícil.',img:'https://images.unsplash.com/photo-1441716844725-09cedc13a4e7?auto=format&fit=crop&w=800&q=60'},
{title:'Fixie Susurro',desc:'Sencilla, como tu risa que me enamora.',img:'https://images.unsplash.com/photo-1505575967456-1b6a9d5b2d54?auto=format&fit=crop&w=800&q=60'},
{title:'Tándem Recuerdo',desc:'En esta vamos los dos, siempre juntos.',img:'https://images.unsplash.com/photo-1506863530036-1efeddceb993?auto=format&fit=crop&w=800&q=60'}
];


const gallery = document.getElementById('gallery');
const modal = document.getElementById('modal');
const modalImg = document.getElementById('modalImg');
const modalTitle = document.getElementById('modalTitle');
const modalDesc = document.getElementById('modalDesc');
const modalAction = document.getElementById('modalAction');
const closeModal = document.getElementById('closeModal');


function makeCard(bike){
const el = document.createElement('div'); el.className='card';
el.innerHTML = `
<img src="${bike.img}" alt="${bike.title}">
<h3>${bike.title}</h3>
<p>${bike.desc}</p>
<a class="btn" href="#" data-title="${bike.title}" data-img="${bike.img}" data-desc="${bike.desc}">Ver detalle</a>
`;
gallery.appendChild(el);
}


bikes.forEach(makeCard);


gallery.addEventListener('click', (e)=>{
const a = e.target.closest('a'); if(!a) return;
e.preventDefault();
modalImg.src=a.dataset.img; modalTitle.textContent=a.dataset.title; modalDesc.textContent=a.dataset.desc; modalAction.href=a.dataset.img;
modal.classList.add('active');
});


closeModal.addEventListener('click', ()=> modal.classList.remove('active'));
modal.addEventListener('click', (e)=>{ if(e.target===modal) modal.classList.remove('active') });


document.getElementById('openSurprise').addEventListener('click', (e)=>{
e.preventDefault();
const frases = [
'Tu amor es la rueda que me impulsa.',
'Si la vida es un camino, tú eres mi destino.',
'A tu lado no existen pendientes imposibles.',
'Cada ruta contigo termina en mi corazón.',
'Eres el viaje más bonito que emprenderé.'
];
const f = frases[Math.floor(Math.random()*frases.length)];
alert(f);
document.querySelector('.love').textContent = '"'+f+'"';
});
</script>
</body>
</html>
