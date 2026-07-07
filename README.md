<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Dharshini S | Cyber Security Portfolio</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,400;9..144,500;9..144,600;9..144,700&family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:'Inter', Arial, sans-serif;
}

:root{
    --serif:'Fraunces', Georgia, serif;
    --sans:'Inter', Arial, sans-serif;
}

html{
    scroll-behavior:smooth;
}

body{
    background:#0a1228;
    color:#ffffff;
    overflow-x:hidden;
    position:relative;
}

.wave-canvas{
    position:fixed;
    top:0;
    left:0;
    width:100vw;
    height:100vh;
    z-index:0;
    pointer-events:none;
}

.lightning-canvas{
    position:fixed;
    top:0;
    left:0;
    width:100vw;
    height:100vh;
    z-index:1;
    pointer-events:none;
}

::selection{
    background:#3b82f6;
    color:#001016;
}

@media (prefers-reduced-motion: reduce){
    *{
        animation-duration:0.001ms !important;
        animation-iteration-count:1 !important;
        transition-duration:0.001ms !important;
        scroll-behavior:auto !important;
    }
}

header{
    display:flex;
    justify-content:space-between;
    align-items:center;
    padding:20px 8%;
    background:rgba(16,27,53,0.75);
    backdrop-filter:blur(10px);
    position:sticky;
    top:0;
    z-index:100;
}

.logo{
    font-family:var(--serif);
    font-size:26px;
    color:#facc15;
    font-weight:600;
    letter-spacing:0.5px;
}

nav{
    display:flex;
    align-items:center;
}

nav a{
    color:#ffffff;
    text-decoration:none;
    margin-left:30px;
    transition:.3s;
    position:relative;
    padding-bottom:4px;
    font-weight:500;
}

nav a::after{
    content:'';
    position:absolute;
    left:0;
    bottom:0;
    width:0;
    height:2px;
    background:#3b82f6;
    transition:width .3s ease;
}

nav a:hover,
nav a:focus-visible,
nav a.nav-active{
    color:#facc15;
}

nav a:hover::after,
nav a:focus-visible::after,
nav a.nav-active::after{
    width:100%;
    background:#facc15;
}

#navOverlay{
    position:fixed;
    inset:0;
    background:linear-gradient(135deg, #0a1228 0%, #1a2a4a 50%, #0a1228 100%);
    z-index:9000;
    opacity:0;
    pointer-events:none;
    transform:scaleY(0);
    transform-origin:top;
    transition:opacity 0.35s ease, transform 0.35s cubic-bezier(0.77,0,0.18,1);
}

#navOverlay.active{
    opacity:1;
    transform:scaleY(1);
    pointer-events:all;
}

#navOverlay.fade-out{
    opacity:0;
    transform:scaleY(0);
    transform-origin:bottom;
}

.nav-toggle{
    display:none;
    flex-direction:column;
    gap:5px;
    cursor:pointer;
    background:none;
    border:none;
}

.nav-toggle span{
    width:24px;
    height:2px;
    background:#3b82f6;
}

.hero{
    min-height:100vh;
    display:flex;
    justify-content:space-between;
    align-items:center;
    padding:60px 8%;
    gap:40px;
    flex-wrap:wrap;
}

.left{
    width:50%;
    min-width:280px;
}

.left h3{
    font-family:var(--sans);
    color:#facc15;
    font-size:16px;
    font-weight:500;
    letter-spacing:2px;
    text-transform:uppercase;
}

.left h1{
    font-family:var(--serif);
    font-weight:600;
    font-size:68px;
    margin:18px 0 8px;
    letter-spacing:-1px;
    background:linear-gradient(100deg, #ffffff 25%, #facc15 50%, #ffffff 75%);
    background-size:200% auto;
    -webkit-background-clip:text;
    background-clip:text;
    -webkit-text-fill-color:transparent;
    animation:shimmer 4s linear infinite;
}

@keyframes shimmer{
    0%{ background-position:200% center; }
    100%{ background-position:-200% center; }
}

@media (prefers-reduced-motion: reduce){
    .left h1{
        animation:none;
        background-position:0% center;
    }
}

.left h2{
    font-family:var(--sans);
    color:#facc15;
    font-weight:500;
    font-size:1.3rem;
    margin-bottom:20px;
    letter-spacing:0.3px;
}

.left p{
    font-family:var(--sans);
    font-size:17px;
    line-height:30px;
    color:#ffffff;
}

button{
    font-family:var(--sans);
    margin-top:30px;
    padding:15px 35px;
    background:#3b82f6;
    color:#0a1228;
    border:none;
    border-radius:30px;
    font-size:16px;
    cursor:pointer;
    font-weight:600;
    letter-spacing:0.3px;
    transition:.3s;
    box-shadow:0 0 20px rgba(59,130,246,0.4), 0 0 40px rgba(59,130,246,0.15);
    position:relative;
    overflow:hidden;
}

button:hover{
    background:#60a5fa;
    transform:translateY(-3px);
    box-shadow:0 0 28px rgba(59,130,246,0.65), 0 0 55px rgba(59,130,246,0.3);
}

button:active,
.card:active,
.achievement-card:active,
.contact-links a:active,
nav a:active{
    transform:scale(0.96);
}

.global-ripple{
    position:fixed;
    border-radius:50%;
    background:radial-gradient(circle, rgba(250,204,21,0.55) 0%, rgba(59,130,246,0.35) 60%, transparent 75%);
    transform:scale(0);
    animation:globalRippleEffect 0.7s ease-out;
    pointer-events:none;
    z-index:9999;
}

@keyframes globalRippleEffect{
    to{
        transform:scale(4);
        opacity:0;
    }
}

@media (prefers-reduced-motion: reduce){
    .global-ripple{
        animation:none;
        display:none;
    }
}

.right{
    width:40%;
    min-width:240px;
    text-align:center;
}

.right img{
    width:320px;
    height:320px;
    max-width:100%;
    border-radius:50%;
    object-fit:cover;
    object-position:top center;
    border:5px solid #facc15;
    box-shadow:0 15px 40px -10px rgba(250,204,21,0.45), 0 0 0 1px rgba(250,204,21,0.3), 0 0 45px rgba(250,204,21,0.25);
    animation:photoGlow 4s ease-in-out infinite;
}

@keyframes photoGlow{
    0%,100%{ box-shadow:0 15px 40px -10px rgba(250,204,21,0.45), 0 0 0 1px rgba(250,204,21,0.3), 0 0 45px rgba(250,204,21,0.25); }
    50%{ box-shadow:0 15px 40px -10px rgba(250,204,21,0.6), 0 0 0 1px rgba(250,204,21,0.4), 0 0 65px rgba(250,204,21,0.4); }
}

@media (prefers-reduced-motion: reduce){
    .right img{
        animation:none;
    }
}

section{
    scroll-margin-top:90px;
}

.about{
    padding:80px 8%;
}

.about h2,
.skills h2,
.projects h2,
.contact h2{
    font-family:var(--serif);
    color:#facc15;
    text-align:center;
    margin-bottom:40px;
    font-size:2.4rem;
    font-weight:600;
    text-shadow:0 0 25px rgba(250,204,21,0.35);
}

.about p{
    max-width:800px;
    margin:0 auto;
    color:#ffffff;
    font-size:18px;
    line-height:30px;
    text-align:center;
}

.skills{
    padding:80px 8%;
}

.cards{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(220px,1fr));
    gap:25px;
}

.card{
    background:rgba(21,32,63,0.7);
    backdrop-filter:blur(8px);
    padding:25px;
    border-radius:15px;
    border:1px solid rgba(59,130,246,0.3);
    transition:.4s;
    position:relative;
    overflow:hidden;
}

.card:hover{
    transform:translateY(-10px);
    border-color:rgba(59,130,246,0.7);
    box-shadow:0 12px 30px -8px rgba(59,130,246,0.3);
}

.card h3{
    font-family:var(--serif);
    font-weight:600;
    color:#facc15;
    margin-bottom:10px;
}

.card p{
    color:#ffffff;
}

.achievement-card{
    background:rgba(21,32,63,0.7);
    backdrop-filter:blur(8px);
    padding:25px;
    border-radius:15px;
    border:1px solid rgba(250,204,21,0.3);
    display:flex;
    align-items:center;
    gap:30px;
    max-width:700px;
    margin:0 auto;
    transition:.4s;
    position:relative;
    overflow:hidden;
}

.achievement-card:hover{
    border-color:rgba(250,204,21,0.7);
    box-shadow:0 12px 30px -8px rgba(250,204,21,0.3);
}

.achievement-img{
    width:160px;
    height:auto;
    border-radius:12px;
    flex-shrink:0;
    box-shadow:0 10px 25px -8px rgba(250,204,21,0.4);
}

.achievement-text h3{
    font-family:var(--serif);
    font-weight:600;
    color:#facc15;
    margin-bottom:10px;
    font-size:1.3rem;
}

.achievement-text p{
    color:#ffffff;
    line-height:1.6;
}

@media (max-width:600px){
    .achievement-card{
        flex-direction:column;
        text-align:center;
    }
    .achievement-img{
        width:140px;
    }
}

.projects{
    padding:80px 8%;
}

.projects .cards .card p{
    color:#ffffff;
    margin-top:6px;
}

.contact{
    padding:80px 8%;
    text-align:center;
}

.contact p{
    color:#ffffff;
    font-size:18px;
    margin-bottom:25px;
}

.contact-links{
    display:flex;
    justify-content:center;
    gap:25px;
    flex-wrap:wrap;
}

.contact-links a{
    color:#3b82f6;
    text-decoration:none;
    border:1px solid #3b82f6;
    padding:10px 24px;
    border-radius:30px;
    transition:.3s;
    position:relative;
    overflow:hidden;
    display:inline-block;
}

.contact-links a:hover{
    background:#3b82f6;
    color:#000;
}

footer{
    text-align:center;
    padding:30px;
    background:rgba(16,27,53,0.7);
    color:#aaa;
    position:relative;
}

.reveal{
    opacity:0;
    transform:translateY(28px);
    transition:opacity .7s ease, transform .7s ease;
}

.reveal.is-visible{
    opacity:1;
    transform:translateY(0);
}

a:focus-visible, button:focus-visible{
    outline:2px solid #3b82f6;
    outline-offset:3px;
}

@media (max-width:768px){
    nav{
        position:fixed;
        top:72px;
        right:0;
        flex-direction:column;
        background:rgba(8,18,32,0.98);
        width:60%;
        height:calc(100vh - 72px);
        padding:40px 30px;
        gap:0;
        transform:translateX(100%);
        transition:transform .35s ease;
        align-items:flex-start;
    }
    nav.open{
        transform:translateX(0);
    }
    nav a{
        margin:0;
        padding:14px 0;
        width:100%;
    }
    .nav-toggle{
        display:flex;
    }
    .hero{
        flex-direction:column-reverse;
        text-align:center;
        padding:50px 6%;
    }
    .left, .right{
        width:100%;
    }
    .left h1{
        font-size:48px;
    }
    .left p{
        font-size:16px;
    }
    .right img{
        width:220px;
        height:220px;
    }
}
</style>
</head>

<body>
<canvas id="waveCanvas" class="wave-canvas" aria-hidden="true"></canvas>
<canvas id="lightningCanvas" class="lightning-canvas" aria-hidden="true"></canvas>

<header>
<div class="logo">DHARSHINI S</div>

<nav id="mainNav">
<a href="#home">Home</a>
<a href="#about">About</a>
<a href="#education">Education</a>
<a href="#achievements">Achievements</a>
<a href="#inspiration">Inspiration</a>
<a href="#skills">Skills</a>
<a href="#dream-company">Dream Company</a>
<a href="#projects">Projects</a>
<a href="#contact">Contact</a>
</nav>

<button class="nav-toggle" id="navToggle" aria-label="Toggle navigation menu" aria-expanded="false">
    <span></span><span></span><span></span>
</button>
</header>

<section class="hero" id="home">

<div class="left reveal">

<h3>Hello, I'm</h3>

<h1>Dharshini S</h1>

<h2>Cyber Security Analyst</h2>

<p>
Passionate about Cyber Security, Ethical Hacking,
Network Security and Digital Forensics.
I aim to build secure digital systems and protect
organizations from cyber threats.
</p>

<button onclick="document.getElementById('about').scrollIntoView({behavior:'smooth'})">Explore More</button>

</div>

<div class="right reveal">
<img src="data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAQDAwQDAwQEAwQFBAQFBgoHBgYGBg0JCggKDw0QEA8NDw4RExgUERIXEg4PFRwVFxkZGxsbEBQdHx0aHxgaGxr/2wBDAQQFBQYFBgwHBwwaEQ8RGhoaGhoaGhoaGhoaGhoaGhoaGhoaGhoaGhoaGhoaGhoaGhoaGhoaGhoaGhoaGhoaGhr/wAARCAKUAlgDASIAAhEBAxEB/8QAHQAAAAcBAQEAAAAAAAAAAAAAAAECAwQFBgcICf/EAFEQAAEDAwIDBQUFBAgEBQIDCQEAAgMEBRESIQYxQQcTUWFxFCKBkaEIMkKxwRUjUmIkM3KistHh8BZDgpIlNGPC8VNzF2SDoyYnNVSEk7PS/8QAGwEBAQEBAQEBAQAAAAAAAAAAAAECAwQFBgf/xAAzEQEBAAIBAwIFAgQGAgMAAAAAAQIRAyExQQQSBRMiMlFhcUKBofAUI5GxwdEVM2Lh8f/aAAwDAQACEQMRAD8A6SBhGQlDkgei8b2mtOFCrm/0mid1D3j5sP8AkrDqq66O0Oonf/mmj5tcEVMYfcd1xkBR5sHGP4cj6JyF2WnVzOQQilaC2Hxxj81lpHG5PmR+ScacB3lghJHidsHGR5I9ILnYzjx+qKnUkhdM3zaMfVWwGGnqC3n8VT0AzLHnPUZ+KuM+4MdARnzWQUrMtZnfkMeSpuLHZpqY/wAJfz9QVePBLG6vHp8VTcUsJtzCfwl/+EINhYXZZGR1wugMPuj0XO+HXfuYT4tH5Lokf9WzzARilhGgBhGVpkRSgkpQRASuSTzRoCcgEOgRlEAHzSsosBAIC9EEeMoEIBhBDkgigERR5QzuiEEIsdUtAhA2lBAjHJHyRRJQaiGEoHCA8JJ5pWUk+aABFhGi5oBySspCMIDykkZSgUaBvqljkhhAIgiESVhEUUSLKPCCAuiJKwhhVSCeaLKUQESA+SGUEEBZ3QyeiGAUECw7zSSUQRoCyhnzRokB5RZRoYQAlBBAIDRIIkUoI0lGgPHmiQyiRB80MboZ2RhQGBsgjQQcK1JJduizsiPNaU4FW3luYqV3LTVw/D3sfqp7TlQruf6Hn+GaI/32oJELC7IB680uUe6zbkf1/wBUqIYe9vLcfqjkAO2+x3+n+Sy2hEffHIcx5pyIBzsg76Sie3J9/cYP5p1jSHsGOYwD4op6kdgBw/j6+GFbln7puM4yQqamy3VnnqB8lfRj90N/xA4KlCGDWxreXvYyqviAB9vd5Pdj00/6K2jBy4Ab6z8VV3ka6F+M/wBYf8JSDQcOOHs1Of5G/kuiwn90w+QXNOF36qClP/pt/JdIpjmnjP8AKFIxUgFGkjwSwPFaYBKRYR4RA5ckEYCPogSjAQQCA0eyARoC5IkZRICwgj9ESAIIsoIDRokOqAigN0ClBAWEMckaPCAuSLCPxRhAkhElIIpJCPkjwjwgRhGUrGElAEaGECEQOSSUoosIosIcuaNBASIoykqkA7osYRoIoIkEaAkDzQRoCwhhLARFAk7oYR4KIZQBBHhAckBYRgIwjx1QIIQwlYyhjCKThGAjKNAWNkOiBQRBIwEEYQDoghv0QQcICJL8kXVaXYAKvvu1pqnDm1rXfJwKsgMKFeW6rTXD/wBB/wCWURNYQZHHPM4+v+qQSSzOfvbeaOF37oOG+QP0OU65v7pmMA94c+Sy6IkWXafMnH5p4DIi22z/AKJDXafAFr/zCdA5YdndRRtbzO4wB8VetaO72Oc438FSYOgjfPQq4YfcwBt69cIh3Qe/w33QTn4qsujCaSUY/GP1Vgw4nbk/hz8VFrmj2aozz2OfioqTwqf6BTjwaF02iGaaL+yuX8JuzQQ+WR9SuoW45pIvRSd2MkoDASggOaNaYABHjdBGiCRFGiQBElAIFASMFDCAQEUEeEEA9USM/RD0QJwh5JWPNABAkhBKxlDG6BHJGjwgR4IAjKJGCgGESUEEBIZRosZQDKGUWEaAZRc0rCAwEUMII0EBc0RSkRCBJRFKx4IYVCMeCGPFLwggQQklOeqS4IpKGEePJK2CITsglDHgggMbIsIxsjCBOEWPJLRKAuiIhGjG6oRhDJThASCigEMIBAbqgsIxsjQQEgUMI0BAJSACPCgLCCPogqOEYRFOEc0khaQWVHuDddBWNHWCT/CVISJRqhlb4scPoVFNW5/fUcTiN3RMPzAUtzcw51biT58lBsozbqM7nTCzPyCnvP7p4PQ5z8ll0RXt0mUc+R+qlBvu+WAcJhzDref4m/5p8ZDGgk/dG6gWG5B07gkAfRWwbmEAHGHYI8FUMGY3luwG/wBFbxHVFJ0GA78kBAYLfJzh6Jqrbqpak7ENaD/eCkge/g88g/TH6IqtgZS1YHWL543UEPhF2KUN8HuH94rqlrOaOP4rk3CrvdlbyxM7811eznNEz1KkZyWOEMIwjWnMSCCCA/RFhGggGPmgUOiBQEhlFzRgIAgQhhAoCRhDmjRQR4RI8ogckko8oigPmERCCGEUSCPCGEBBH6oYwhhAfNBABHhASGOaPCMIC0oEJQCCBI80MI8FAjCAIuqP80W2UBEII8IcwqCQwjIQwgSjxsjIQ5clAktyixjmlhA7oG8JWEMIYVAxhER4JSCBP0QxhGgAiAgjAwgRhNKCIhHhEQqCwhhHgoIB03QIQxlAookAEoIBAWEeEMIIBhBK0nCCDhZakEeKe6JDlpDWEYbnbx2SgPFG0YcPVBX2F2m30YJ/5eCPTIU5/KXYDbYfA/5KvsYzTQjBwHvbt5PKsXgh7geeP8/81h1hBPLb8JOUtjjpA2wNvgkZB0kdGnbx2S4wCzYnmMqBxrdTD1yN/qrOjy5pxvqjGNvJQWgDb3TvyyrClGY48bYxgeiB0feDh5fn/qjqQXxVIxguhJ+iUxpw7PLA2PjlOyN9yXAB1Quz5bFBQ8L7Szt8JT+QXWLN/wCTaPNco4aIFZVD/wBQH+6F1ey70vxU8s5LMII0CqwJHhBGiCwhlGgUBIIwi3QEEeUCiQH0Q6oc+SCKLkgUZCLCA+aCACUAgSECjKJUF1Q9EaNRSUaAG+UaoCGEeEEQEMZR43RIBhGggFAYRFKRFVRZQz4o8I8IE4RY3S+SCBOEWPmlFHhENowlEDCCBOUWUo7o8IhCARkIsYQFhHhBGgLCGEaGECcI8bI8eCGECUY3QAR46KqJHhHyRICxhEQlIsICCBSuSBQJ3QR4SkCUY5o0aoPogi5IIOGdEhyMFDYrSEJQ5hA7IsqCus2pkcrM401Uo/vn/NWTj+9AJ5tdn/fwUC2jD64fw1j8fENP6qxczMo6gE5+qzXWXoYDSTuNyCfXZORjSdycbAj1SMEBm25aR9EogsyNtnA/IqKktaNWDvkKyowNLR0BICgMx3o6DZT6XaLyDjt4c1A+Tzyd+Z26ZUh4LiBzJZg48CCo43HPPTKlEkys6Z2P+SDN8NkftCpHm0/RdYsv/l3DzXJuHxi7VI/lYfzXV7GcxOHoozl2WyJLA8UOqrmIBKCLCPCAjz5I8IIY8UCSN0AEZAJQA5qqIDdDCXgIEYQIR43R4RYwUB4GEkhKQI3QJzj0QygRuggCAGyGyPGyAkEEaKARosIIBhBGgR8EBBGiCPKA0aJBAaCBQQBHjdJRoD+CAARdEYQHgIIjzQRA2QwgggLGEXilZRKIJEUpDCoSAgQEeEBjwQFhGUaI7qgkrHJFjCPKAYQxhBBFEi2CPqiKKAQQRhAMIY3RoHYIgsYRI/VDHzQF0RhBAIo0EAgg4OiyldEkrbI8oE7IkDuEEK3nTWXPPSpafnG3/JWmQHuJ6b5+KqqQYuF0aRtmB3zZ/orRwJeM9WE/JYrpOxtxw+Mgb9c9Ug53+Hx3S2D980nfCN22QRk74Phuo0fbtKSNvf38t1ZUWXNdjHN35qvjz3jieefmrSk3LsHLdbv0QO4HdtA5E5z8FJbhskIB21tamCP3YA5J3O8Wro8Zx1UGcs/uXyoH/pj6OK6lYDlr/Rcsoh3fEczB/A76PXT+Hne87+yp5ZrQAII8IfBaYBBAoEYQBFulIsIE4KNBAIDBQJRIwgCCNFtlAMIEYRoFAgoYSs7oc0UlBGgQgSUYQKHJAeUXNAo/REGERQQOyAsogUaLG6KVlHz6pIQ9VQtBJQCBWEXhhDKGUB7oAIBKCgLdGizlDxwgNEj2+CJRBckaBQOyAdEOqAKHNVBkpJRowgTuhjdGhyQJQRlDkihhDCM8ggN1QXqiSkRQJRhFhDCKMFA+aAQ80BBH6IckSoCCCPmVAAUEEEHBwiPkkg/JKHRbZGBlLDUQHgnAMoIFO3/xauB6wQO/xBWhAaWN6OYfmq5oAvEo5a6Jp+Uh/wA1ZPBzCD94s6fFZrc7IzyO9aT1G6WwA95tuAcJD9pI8jUCOSJx0Su8yRz8lltJZvK0k4ccA9VaULjl+oY94/kFUxn3hvggj9FbUZDTKwj8f+SgedsOocHkYTrnYEZGTh2UiUnMpO2l4I8+SVKSGtJ6DogoGjRxS/0lGf8AqC6Tw+7976tXOqhmnidhOxLpQcegK6FYD/SGeYTyzWpGOqCNBVgRR4yiRoouSIhKRYVQRCAwgUSijSkkI0AKJHlAoAggiKqBjwQRZRKAwggdyiyqodESIlFlQLyi1JOUOaIXlDPikZR5VBo8bpKNAeUEXVAIo8o+SJFnxQHndGElGNkC0MogUFAaP8kQRoAlIgh0UQCERRoIEoJWERCqAErokoz5IAUQQO6CAIIwggSjOyMInKqCCLKAyijx4IsbI0M+CAYQwhyQQJPNDCVgIEdQgSEaGEFQEEEFB59EvLp0TjXrJ2h8ZjjkoqeokaW+7NVyEEj+VvQegC0kchOFqXc2xE5p+adBURknin2vGyqosjgy8056vpJW59HNP6q1f/Vw/wBrGfFVFUdF2trvFk7P7oP6K2ccU7DnJDwfVZrc7GJ9mxnHJJfETJu7OdJ/NLmA0s33yR6I+YG+dh+ay2EedYbncFXFI4NEp54cPyCqWAiXIPIg5VnC4EuaRu4gfooJ0x1PJHLbKVIwFm3hkhIkAOSCM6yCPBSBhsR1AuyNseSCgr3aeIac9XPP1YFvLCf6RH5rAXV7Rf6LSRnW04z/AC4W8sR/fxeqeUrX9EEaCrBOEEaHVASCNDxVQRReqNEQijQwUBulICRYSklQFyRdUfqj81UJ5IuSMpJUURKCJBARKIlEUWSgPKGUnKNVC0abB890C8AEnogdyhnwUOSra3ZpyeRWP4p7VeF+DWn/AIgu1PSSD/lB5fIf+gbq6G8zlNvnjjbqkc1o8SV5+q/td8GxS6KWiutY0Hd8cLWjHjhzsrmnGn2tbpPc2ngq000lFHj/AM44mR3j7rTgfMq+zJNx7Ljqmykhm+BnPLbxTjXh2SNxleZeyf7R0PF90FtvtI603Bo1Ma5xMcmRvpcdwfLJC9I0NSJKSJwH4eSllndUxGAm+8A3PJLbI07AhQKAR8ghnZDKAwgiCMqKNqNEEaILdEjPmggA3QQR80BYRI0EQSNGAggSleqJAooxyQwghlVRaURGEsHKHREI6I0EMqgHdEjQUUDyQQQ9UBZQ2Q6oIAQglYQQeZItyp0QVdA4k4OxHirKPkFuspTN+fJSGNCYjCkN2QQ65oFfaHeFQ9vzjKsXOcaQA7Y5H4quuh0vtj/CtYD6FrgrA7UxcSOfL4hZrePYUw1RtI294/kiJzHlxGrJH+iEg/cM3GQ4DP0SCQ6J2cbux9Fls/GC/I6jCnxAd/nPUZA6HKgQ5A575G6nxjRI488D57qCzePfkI2JdvspAGluCeWd/gmhkB2++PknSf3Wc75G3jsgzd7ha272+YNw4d2M48yFurJtLD6hYy/jEtC855s/xlbKzDDoz5hEbQBHhDCHqqwLCGEZwk5VQEMeKNGgTjdJKXhJ8UBIwgRhEUUCiRIZUQZRZSSUklFKJScpJKBciDJRZykk7Ii5AZO6LKTnKLPiqFZ3Rk4SQU1PO2NjnPIACBNRUMhY58jg1reZJ5LiPaN9oawcHGSmjcbjXge7TQvA0/2j+H47+S599oTt2qKSsqOGuGJ+4khyKypYd2bfcHnvv4evLx3X3SUyuk1EyyEnLjkjzPiV1xw2zctO08Y/aH4w4iMrG3J1ppDkez0J7vA8HP8AvH6LjFdfJbhO4mV5LnZc5zsucfEk81TVNW9zdAeSScknxUNkpzpbsOp6ld8cZHG5WtdSV8Ucehzs56E7E/qpDbq0DSHaGDo3YLIiQs+7zRsqCHtzuBvueq2zt0S2399I5joDoHiT/vC7Lw99pXi6xW11G2anuQDNFOa4HLCOXvNwSOm680U9wALdZyQ7O/Qq9ZVMlaw8yHZ3P5rOWEreOdj1fwD9qO83AynjCzMbTUrgyoqIHFndk7glhJyMb+7nbdepLFeILtRQ1NO7VG9oc1zN2kEZBB6r5mwXR/s09M6d8T5WuDXtdgtGnGfjkgjwK96dhslNHwDw/DQ1zK1sNHHG+RuwLgPebg7jB6LzZ46dpdx1lrw4eaVlMg5weRS8+K5qcCV1TYKWEUrqiKB6IlEAJQRI0BoIIICQyj9EkoDyhlEEaIJDKB5IDdFBBBBVRjZBEEYQDKCCNAOiIo9kDuiE5R80eESqgjCAQRB5QQQQeTKBtdFForq2OpkxuWwiI/QrQW+YzwtL2lj2nS4HHMeiyFj4Ntdt0kQuqZsby1Dy8k+nIfJbGkgbC0NYAAPBMd66sRYxjCktHkmIuilMGy00gXoaaWmfj7lZAf72P1UqN+qmfjkC7AKi8QA/sqQ9WyRO+T2qZECQ8ciSQfqs1qGgSKc75wdkY3YBgYyMFFkd0ATz5oNd+7bk597b0WXRIyAA0bEDf6KfDuSHeYVawl5aM4JBCnxP2GSOuc/BBb5zknq0Y81IZgxAk8gQokJ1FmeRapFO8uY0EZP+igo+IXFsVLt93x8nrZ2jkw+axnEgxRU7hvs/n6grY2g5YwhEbgfRDCDPutz4BGtOZJCGEr5okBdd0aJBAEnCGURKAE4KSiJ5pBO6gUThJJ8URd4psuygWXbJBcEklIL1A4XJBemi/CbMhVVIL0nWo5kQ7xA/q8EC9Ma0etVDjpQ0EuOAAuT9sXabHwTwtWVMT2urpcxUrM/8w8ifIYJPp5roN7rPZ6QaTgucBnwHVeEvtD8YSX3jGagY8tpbd+5awcg/HvH5YHzWsZuluo43fLnLPLLNUSOlmmeXPe45L3E5Lis8C6Zznnn08lNrS6skOnk1+wHhhN6W00buWSNQP0Xrkea1WysLBuMvfsAlMgLAOpwpopy6TvXfdHutRHTp2WmUOUaWbDUfzKjj3QXO33381YFgaPe22UZ0WsgYwOgVDDJZHvyDhXFFWd27AI22Hr4qE2nDQPBoyUzG9zJsjbyUGjbWP7xpz7oO/iSuwdlXavcuBaqibT1LvYp3aaqBx93PRwHQ4+i45DA72ZruTvADkpFJI/2mJpyMvDiOuFjPHbphlp9RuBeNqXiy2MnhezXpBLQ7mVsmnK8kdgvEkbaCnDHuFVBhkrCdnMO7T9cfAL1VRVAmhY4EEOGQfFeN6bE8HCWCmQc+iWCiHfREcpIPwShuoDQ9UOqPCoNGBlFhHv1RAwiI80eUMbICwgQhlBAXVAIcuSCKNDCIowiC6o0PVEeiKG6MEoiiQKCMBJalZVBpKPfojQENkEeUSAZQQ3QUHlyBwyFbw7gLlPD3GN84if8A+EWKIQA4dUVNSWxt+IbufILpdr9sbGPbn08kp3xCxzGjxG5JP0THKZ9Y5y7XsLdgpbGqPF0UyMZWmkC/x6rLWnwj1fIgpQkDWHfGXalKu8YfZbgMc6aT/CVVsGunicSMuaD5btUrWJ0HLATzBPTzSWgmI9dLslEHDQ0O5kndIhf7sgcc7bbLLolRnBjdqG7uvT/eFNa7DyQDy3GFWE4jGDkg5OVYxFrWEkjJxv8AFBcQv9xrmjAwPipEAJLWjYOOyhxOApw3kAdyrGLbSTyBz9f9VBR8RsJtsYP4XSY+Q/yWpsbs08J8Wj8lmr/vQHB5SH/Cf8le8Ov1UdPvzY38gg6LFvGz+yEvKbpzmCPzaEsrTkCBCJAnCAYSTzRoiUCSUglGSkuKgS5yQSg47pDjjqoA52E2XonFNkopbnJtz0ku3TZcptdDL8JsuRuTZKbUkvwUO8SHO3Tbn4TYkCRHr22Ki6/NJfLoGeg5q7TSk4prO6gc55wxgcXE9G4wfocr5xcd1b6m+V9RI/W6ad79XiS4r3p2o3b9lcO19Y2TQ5lO8EHxLTjC+et1ldVVDsjBzsu/G559lbA4e+eTtiE17FNVyHSCW9fQqY2lLA1wWy4N9nfVs9phaXNOQWnf/fqt58ntmzj4vflqsheoXUmmmY3AgYGux1PMn6qgjmIdvufyXZeIOF6Wpq5XRloa5xcGnYnO4BWAu/C1RSPJbjSTtgYWOPml6OnL6fLHrGb7wvdl+5J2HgnGY1jq7zSJqWSEkEEAdR1SGZ5NBx+a9Usrx6
