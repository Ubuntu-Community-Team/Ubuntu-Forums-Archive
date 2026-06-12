---
title: "Ipmasq, dnsmasq and firestarter"
date: 2006-09-13
forum: Networking &amp; Wireless
---

### Post by bastupungen on 2006-09-13
Hej!
Jag körde tidigare med kombinationen av firestarter+dhcpd3 för att dela ut internet till mina andra datorer i nätverket. Detta funkade men inte klockrent för ibland funkade inte internet utan man fick pröva några gånger i minuten. När det sedan börjar funka så funkade det bra. 

Så jag tänkte byta program att köra på, och hoppas att detta fungerar bättre. Efter många om och men och brutna knogar ](*,)  så fick jag ipmasq+dnsmasq att fungera. Dock så har jag då ingen firewall på min server, vilket känns lite dumt. Så jag installerar om firestarter och startar den. Vilket gör att internetdelningen slutar funka. Jag prövar att starta om ipmasq och dnsmasq utan resultat dock så när jag stänger av firestarter helt, och startar om dnsmasq och ipmasq så börjar det funka. 

Vad beror det här på? måste jag öppna upp några portar för att det ska fungera med firestarter eller ska jag använda något annat program för att få internet delningen att fungera?

Notera att jag inte har på internetdelningen eller dhcp:n i firestarter.

---

### Post by bastupungen on 2006-09-13
sorry, wrong forum!

How do i delete this post?

---

