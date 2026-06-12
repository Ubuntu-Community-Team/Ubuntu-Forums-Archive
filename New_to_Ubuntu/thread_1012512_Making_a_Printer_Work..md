---
title: "Making a Printer Work."
date: 2008-12-15
forum: New to Ubuntu
---

### Post by dragonfellow17 on 2008-12-15
I have a Lexmark Z816 and can't get it working in Xubuntu most of the problems I have had where fixed by searching. But a thread I found on the forums someone said to use CUPS(it's installed and working) but I need drivers for it. I also have a Lexmark P3150 and a HP P5C 1401 All in One that I could also use. Would the scanning also work? I just need a printer that can print but scanning would be good too. I could also buy another printer if none of them will work. The drivers for the Z816 on linuxprinting.org said that they don't work and its a rpm file and I can't open it. So what can I try/do next.

---

### Post by jbrown96 on 2008-12-16
Is the Lexmark Z816 wireless? My dad has a wireless one and as of about 8 months ago wireless printers don't work in Ubuntu, but things may have changed. From what I've experienced, HP products work fantasitically in Ubuntu. In fact, if they are connected via USB, no setup is required. You may need to install a program called hplip (available in Synaptic in System-->Administration-->Synaptic) that will manage the hp devices. 

As far as scanning goes, there are a couple programs that I had my dad use. He scans a lot of insurance applications (into PDFs). Xsane is the default and I think it automatically installed. It works fairly well, but my dad found it confusing, especially for multi-page documents. If you are looking to do very basic scanning (i.e. PDFs, not photo quality), try a program called gscan2pdf (or something very similar, the name escapes me). It's also available in Synaptic, and it's very simple.

---

### Post by Sef on 2008-12-16
> The drivers for the Z816 on linuxprinting.org said that they don't work and its a rpm file and I can't open it. So what can I try/do next.

OpenPrinting says[ your printer]("http://openprinting.org/show_printer.cgi?recnum=Lexmark-Z816") works partially.  As for the rpm file, check out [How to Install Anything in Ubuntu]("http://amitech.50webs.com/installing/index.php.html").

---

### Post by dragonfellow17 on 2008-12-16
Ok so I installed it with the scrips. Now how do I set it up because its not showing the drivers in the printing drivers menu or in CUPS. EDIT: No it's not wireless

---

### Post by dragonfellow17 on 2008-12-27
bump

---

### Post by 5BallJuggler on 2008-12-27
Have a look here:-

[http://openprinting.org/show_printer.cgi?recnum=Lexmark-Z816](http://openprinting.org/show_printer.cgi?recnum=Lexmark-Z816)

Phil

---

### Post by dragonfellow17 on 2008-12-28
The Cerqueira.org's driver page, and Lexmark's Linux Driver Kit page links are not working.

---

### Post by dojida on 2009-01-07
I have also been trying to get a Lexmark Z816 working. I followed all the instructions from g2g591 in his July 21st 2007 post, and am stuck on the last line : sudo /usr/sbin/lpadmin -p Z810 -E -P Lexmark-Z810-lxz810cje-cups.ppd.gz -v z810:/dev/usblp0
I just keep getting "no such file or directory". This seems to be where the other correspondents get stuck as well.

---

