---
title: "No 3d acceleration for me in 10.04"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by bcoffield on 2010-08-22
Hi all,

Ever since upgrading to 10.04 my video performance has seriously dropped.  If I turn on the first level of desktop effects my comp becomes basically unusable.  I have been using ubuntu for a few years now and have never had the problem.  

I was trying some things out yesterday and nothing worked but I came across this page [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD) that told me how to see if hardware acceleration was enabled ( glxinfo | grep "renderer string" ) and it turns out mine is not.  When i run that command I get the result  

OpenGL renderer string: Software Rasterizer

I have an ATI radeon x600 card in my laptop.  I'm more that happy to provide any information (provided you tell me what commands to run :)

Please help!  Thanks!

---

### Post by utnubuuser on 2010-08-22
So far, the only way I've been able to get proper performance from my x00 ati card in 10.04, is to turn effects off in Appearance, then switching on compositing with Alt+F2>>gconf-editor>>Applications>>Metacity>>General>>compositing_manager

---

