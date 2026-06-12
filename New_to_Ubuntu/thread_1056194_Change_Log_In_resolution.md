---
title: "Change Log In resolution??"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by MaximoMilkman on 2009-01-31
Hey guys my log in resolution i believe is to small... when i type my username in the letters are like 1pt font i have a 26 inch vizio as my monitor... Ubuntus resolution is set at 1360X768 @ 60hz but my login screen seems messed up.. i was reading here..

[http://dkseto.wordpress.com/2008/10/31/ubuntu-81-login-screen-resolution-problem/]("http://dkseto.wordpress.com/2008/10/31/ubuntu-81-login-screen-resolution-problem/")

It said to edit my xorg.conf under the MODES section... but my MODES section is non existent.. this is what my xorg.conf reads...

[COLOR="Red"]Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection[/COLOR]

as you can see there is no MODES nor is there a subection display.. i have no subsection display? should i make one.. also someone was saying ubuntu reverts to a VESA driver with some Intel graphics cards or something.. because i have an INTEL integrated graphics card so is there a way to tell if ubuntu is using that or a vesa driver??

---

