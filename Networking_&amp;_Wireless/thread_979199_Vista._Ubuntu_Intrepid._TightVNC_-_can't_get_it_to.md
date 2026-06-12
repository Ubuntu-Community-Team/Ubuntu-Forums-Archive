---
title: "Vista. Ubuntu Intrepid. TightVNC - can't get it to work."
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by Roasted on 2008-11-11
I don't know what I'm doing wrong, but I was instructed of the following. My goal is to allow my Vista Home Premium laptop to control my Ubuntu Intrepid 64 bit desktop.

I was told that on the Ubuntu machine to go to system - preferences - remote desktop and check the box to allow users to control my computer.

On the laptop, I downloaded and installed TightVNC. When I run it, it asks whom I want to connect to. I've tried my desktop's IP along with the name it gave me under sys-pref-remote desktop, which is "vinagre jason-intrepid:0"

What more do I have to do? The vista laptop just isn't picking anything up.

---

### Post by 9999999999 on 2008-11-11
I don't know... Did you ping the ip address of the ubuntu machine to verify the connection?

---

### Post by Roasted on 2008-11-11
Yep. I'm on my laptop and I can ping my desktop fine.

In fact, my Ubuntu desktop is running a samba share, and I can log into that just fine without any issues whatsoever.

---

### Post by 9999999999 on 2008-11-11
Remote desktop is enabled on a per user basis (unlike samba). Is the user that has rd enable currently logged in on the ubuntu machine when you try to connect from the vista box?

---

### Post by Roasted on 2008-11-11
I'm on my Ubuntu desktop right now.

IP is 192.168.1.101
Computer name is jason-intrepid

I tried using remote desktop in windows along with tightvnc viewer.

I tried:

192.168.1.101
jason-intrepid
jason-intrepid:0
\\192.168.1.101
\\jason-intrepid

etc, etc, etc...

---

### Post by Roasted on 2008-11-21
Any input? I still can't figure this out and it enrages me when I hear about people saying how easy tightvnc is to use. :(

---

### Post by jonobr on 2008-11-21
Hi 


A frequent poster to this forum setup this on a website he owns

[http://prash-babu.blogspot.com/2008/06/how-to-remote-control-your-ubuntu.html](http://prash-babu.blogspot.com/2008/06/how-to-remote-control-your-ubuntu.html)

---

### Post by Roasted on 2008-11-21
I hate to be a stickler, but that's not tightvnc, though... and that's been kind of my goal is to get tightvnc running...

---

