---
title: "graphic driver for Intel video card"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by Elya on 2009-01-07
Dear All, 

Could you please advise which video driver I should install? 
My video card is 

lspci -nn | grep VGA

00:02.0 VGA compatible controller [0300]: Intel Corporation 82Q35 Express Integrated Graphics Controller [8086:29b2] (rev 02)

Thanks in advance

---

### Post by mapes12 on 2009-01-07
Have you tried your video card with Ubuntu? It may work as it is. If you haven't installed Ubu yet then try running it from the Live CD and see if graphics works OK. Also, which version of Ubu are you using?

---

### Post by halitech on 2009-01-07
typically the Intel cards "just work" and there are no extra drivers to install or use.

---

### Post by Elya on 2009-01-07
Thanks for your quick replies. I do have ubuntu linux intalled and it 'just works'. However, I have a problem with visual molecular dynamics package. 
It works only in the text mode and in the graphical mode crashes. 
It gives the following. 

XRequest.143: BadRequest (invalid request code or no such operation) 0x17
XRequest.143: BadRequest (invalid request code or no such operation) 0x17
XRequest.143: BadRequest (invalid request code or no such operation) 0x17
XRequest.143: BadRequest (invalid request code or no such operation) 0x17
XRequest.143: BadRequest (invalid request code or no such operation) 0x17
ERROR) A TrueColor visual is required, but not available.
ERROR) The X server is not capable of displaying double-buffered,
ERROR) RGB images with a Z buffer.   Exiting ...
Info) VMD for LINUX, version 1.8.6 (April 6, 2007)
Info) Unable to create OpenGL window.

That is why I thought I have a problem with graphics driver. 
Do I need to change the xorg.conf file? At the moment it looks like that. 

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


I would really appreciate any help. I honestly try to find answer myself but I can not. I do not have much experience with linux and I am really suffering. Please, please, help!

---

### Post by halitech on 2009-01-07
what version of Ubuntu do you have installed? Typically starting with 8.04, pretty much anything to do with the video card is automagically detected and setup so not very easy to make changes as (from my understanding) xorg.conf is pretty much ignored now. someone may have better info but I don't think the intel (or SiS) video cards do very well with 3D stuff.

---

### Post by Elya on 2009-01-12
I have ubunti 8.10. I guess it has detected video card. The computer itself is working, but it says in the error massage

 A TrueColor visual is required, but not available.

Command glxinfo gives

name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

Please help me.

---

