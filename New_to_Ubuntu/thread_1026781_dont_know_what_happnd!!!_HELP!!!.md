---
title: "dont know what happnd!!! HELP!!!"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by ppch21 on 2008-12-31
hey... im using a Dell inspiron 640m...1gb ram... 
and ubuntu intrepid 32bit... (do u think i should use 64bit???)
and i just started using ubuntu 1month ago...

the thing is that... i cant watch videos in VEOH 
i cant play games on FACEBOOK and also any webpage with on line games works!!!
have no idea whats wrong... 

i also have problems with open arena... it starts normally but after a few seconds... the graphics just crash!!! 

i already rode some forums... but nothing works... i really need help...
i like ubuntu pretty much and i want it to work... 

i think is a 3d card problem... what u say??? help plz...

---

### Post by bwang on 2008-12-31
Did videos work when you first installed Ubuntu?. Have you tried looking under System>Administration>Hardware Drivers for drivers for your video card? Have you installed flash?
```

sudo apt-get install flashplugin-nonfree

```

---

### Post by ppch21 on 2008-12-31
IT SAYS THAT... and 


ppcastherr@ubuntu:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for ppcastherr: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
flashplugin-nonfree ya está en su versión más reciente.
Se instalaron de forma automática los siguientes paquetes y ya no son necesarios.
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
  libboost-date-time1.34.1 gnash-common
Utilice «apt-get autoremove» para eliminarlos.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.

ANY IDEA???


Ok... it is in spanish... jejeje...

it says that FLASHPLUGIN is already installed... =S

---

### Post by PierreDeKat on 2008-12-31
I'm not sure if I'm on the right track here, but the thing that jumped out at me was something about "gnash-common".

I'm wondering if you have both flashplugin-nonfree and gnash installed at the same time. If so, that may be causing the problem.

Try opening Synaptic Package Manager and searching for "Flash". You **should** have flashplugin-nonfree installed, and you should probably **not** have gnash or swfdec-mozilla or any other flash plugin installed at the same time.

---

### Post by abn91c on 2008-12-31
assuming you are using firefox go in FF3 to tools>addons>plug-ins and make sure shockwave and flash player are listed there

---

### Post by ppch21 on 2008-12-31
FLASH PLAYER THING ON MOZILLA FIXED!!!!
Thanks a lot Guys!!!!!!
it works now!!!!!






what can i do with the openarena thing???
i will send a pic... so u cant have an idea of what happend...

---

