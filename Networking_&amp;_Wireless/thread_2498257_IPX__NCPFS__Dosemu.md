---
title: "IPX / NCPFS / Dosemu"
date: 2024-06-06
forum: Networking &amp; Wireless
---

### Post by achiaramello on 2024-06-06
Buenos dias a todos.
Les comento lo que estoy buscando.
En la empresa donde trabajo disponen de dos servidores algo antiguos, que corren Novell netware (3,12 y 6,0).
Tengo varios sistemas linux que mediante el soporte del protocolo IPX en el kernel mas NCPFS y Dosemu, puedo conectarme a estos servers y correr las aplicaciones alojadas el ellos.
El tema es que necesito actualizar el parque informatico y me encuentro con que el kernel ya no tiene soporte para IPX, NCPFS y DOSEMU estan practicamente si desarrollo.
Necesito saber si alguien ha podido experimentar y hacer algo al respecto, ya que en hardware nuevo, las versiones antiguas de cualquier distribucion linux no funciona.
Agradezco cualquier tipo de orientacion que puedan darme al respecto.


Atte, ARiel Chiaramello




--------------------------------------------------------------------------------------------------------------


Hello, everyone.
I tell you what I'm looking for.
The company where I work has two somewhat old servers, which run Novell netware (3.12 and 6.0).
I have several Linux systems that, by supporting the IPX protocol in the kernel plus NCPFS and Dosemu, can connect to these servers and run the applications hosted on them.
The issue is that I need to update the computer park and I find that the kernel no longer has support for IPX, NCPFS and DOSEMU are practically undeveloped.
I need to know if anyone has been able to experiment and do something about it, since on new hardware, old versions of any Linux distribution do not work.
I appreciate any kind of guidance you can give me on this matter.


Atte, ARiel Chiaramello

---

### Post by currentshaft on 2024-06-06
Run them on new hardware, virtualized in a safe environment with your supported kernel and system architecture?

---

### Post by Holger_Gehrke on 2024-06-06
The two kernel modules aren't part of any standard kernel anymore, but there are developers still working on them and making them work on newer kernel versions. For IPX there's [https://github.com/pasis/ipx](https://github.com/pasis/ipx) and for ncpfs there's [https://github.com/EnzephaloN/ncpfs_dkms](https://github.com/EnzephaloN/ncpfs_dkms). The latter actually uses dkms so the module gets recompiled automatically on a kernel upgrade, for the former some manual work is required after a kernel upgrade.

dosemu on the other hand hasn't been updated since 2012 and might not work right even if you do manage to compile it from source. If dosbox - which is more geared towards running old DOS games than keeping obsolete applications running and has a high overhead because it's emulating the whole system - doesn't have the functionality you need (and I do remember that printing and network access have never been good on it), then you might want to think about running FreeDOS in a virtual machine. In that case you might be able to use the original (DOS-) network drivers and the whole question of Linux drivers for Netware might become moot.

Holger

---

