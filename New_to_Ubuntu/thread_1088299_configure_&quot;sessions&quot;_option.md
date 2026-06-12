---
title: "configure &quot;sessions&quot; option"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by raymondh on 2009-03-05
I lost my option to configure sessions ... which previously was at system > preferences.

Was un-installing WINE thru terminal.  Wanted to do a short-cut and coded sudo apt-get remove wine* (thinking that the * would take out all included in Wine).  Afterwards, I noticed I could not activate AWN manager.  I then decided to take a look at sessions to see if the AWN command was unchecked ... which was when I realized I no longer had my "session" tab.

Any tips on how to undo my mistake and get session back under preferences?

Thanks in advance.

Just to investigate further ... was searching the forum and found a thread involving auto-remove.  To try out, coded sudo aptitude update and sudo aptitude safe-upgrade to see what was removed for installation.  Here it is.

  abiword{u} abiword-common{u} abiword-help{u} abiword-plugin-grammar{u} 
  abiword-plugin-mathview{u} arj{u} cheese{u} dasher{u} dasher-data{u} 
  desktop-base{u} gdm-themes{u} gnome-backgrounds{u} 
  gnome-games-extra-data{u} gnome-network-admin{u} gnome-themes-extras{u} 
  gnome-vfs-obexftp{u} gnome-volume-manager{u} gnumeric{u} 
  gnumeric-common{u} gok{u} gparted{u} gthumb{u} gthumb-data{u} hardinfo{u} 
  inkscape{u} latex-xft-fonts{u} libaiksaurus-1.2-0c2a{u} 
  libaiksaurus-1.2-data{u} libaiksaurusgtk-1.2-0c2a{u} libblas3gf{u} 
  libgda3-3{u} libgda3-bin{u} libgda3-common{u} libgdl-1-0{u} 
  libgdl-1-common{u} libgdome2-0{u} libgdome2-cpp-smart0c2a{u} 
  libgfortran3{u} libgtkmathview0c2a{u} liblapack3gf{u} liblink-grammar4{u} 
  libloudmouth1-0{u} libmagick++10{u} libots0{u} libsoup2.2-8{u} libt1-5{u} 
  libwmf-bin{u} liferea{u} link-grammar-dictionaries-en{u} menu{u} 
  menu-xdg{u} p7zip{u} perlmagick{u} planner{u} portmap{u} 
  python-4suite-doc{u} python-4suite-xml{u} python-gnome2-extras{u} 
  python-lxml{u} python-numpy{u} python-uniconvertor{u} rhythmbox{u} 
  serpentine{u} swfdec-gnome{u} 

Dunno if this helps.

---

### Post by x33a on 2009-03-05
see if you can start it with

alt+f2, gnome-session-properties.

---

