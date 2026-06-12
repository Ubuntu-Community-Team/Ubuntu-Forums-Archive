---
title: "Can't install FreeNX"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by GXice on 2009-05-04
I've gone through [this guide]("http://alandoyle.com/2008/12/16/setup-freenx-under-ubuntu-810-intrepid-ibex/"), but keep getting this error when attempting to install.

```
After this operation, 0B of additional disk space will be used.
Setting up freenx-server (0.7.3+teambzr104-0freenxteam1~hardy1) ...
chown: invalid group: `nx:nx'
dpkg: error processing freenx-server (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of freenx-rdp:
 freenx-rdp depends on freenx-server; however:
  Package freenx-server is not configured yet.
dpkg: error processing freenx-rdp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of freenx-media:
 freenx-media depends on freenx-server; however:
  Package freenx-server is not configured yet.
dpkg: error processing freenx-media (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of freenx:
 freenx depends on freenx-media; however:
  Package freenx-media is not configured yet.
 freenx depends on freenx-rdp; however:
  Package freenx-rdp is not configured yet.
 freenx depends on freenx-server; however:
  Package freenx-server is not configured yet.
dpkg: error processing freenx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of freenx-vnc:
 freenx-vnc depends on freenx-server; however:
  Package freenx-server is not configured yet.
dpkg: error processing freenx-vnc (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 freenx-server
 freenx-rdp
 freenx-media
 freenx
 freenx-vnc
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Can someone help me figure out what's preventing the install from taking place?  :(

---

### Post by tgellen on 2009-05-16
Looking at the errors you're getting suggests you're using Hardy. I've only tested the procedure on Intrepid and Jaunty. I'll try to get hold of a box running Hardy and see if I can shed any light on your errors.

---

### Post by georgeen on 2009-05-22
> **tgellen said:**
> Looking at the errors you're getting suggests you're using Hardy. I've only tested the procedure on Intrepid and Jaunty. I'll try to get hold of a box running Hardy and see if I can shed any light on your errors.

In Xubuntu Jaunty This error appear:

expect denyhosts xdialog
Leyendo lista de paquetes&#8230; Hecho
Creando Ã¡rbol de dependencias       
Leyendo la informaciÃ³n de estado&#8230; Hecho
openssh-server ya estÃ¡ en su versiÃ³n mÃ¡s reciente.
dbus-x11 ya estÃ¡ en su versiÃ³n mÃ¡s reciente.
fijado dbus-x11 como instalado manualmente.
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidiÃ³ una situaciÃ³n imposible o, si estÃ¡ usando la distribuciÃ³n
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.
La siguiente informaciÃ³n puede ayudar a resolver la situaciÃ³n:

Los siguientes paquetes tienen dependencias incumplidas:
nxagent: Depende: libxcompshad3 pero no va a instalarse
Depende: libxrandr2 (>= 2:1.2.99.2) pero 2:1.2.3-1 va a ser instalado
E: Paquetes rotos

And I don't know how to resolve the dependency that apt ask me. I follow too [this instructions]("http://alandoyle.com/tutorials/setup-freenx-under-ubuntu/comment-page-1/#comment-134") withouit success.

Thanks

---

