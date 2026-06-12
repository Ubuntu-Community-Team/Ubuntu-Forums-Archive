---
title: "ATI Radeon HD 6450 driver setup"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by imaginedtruth on 2011-03-30
I everyone. I am new to Ubuntu, and just installed and updated Ubuntu 10.10 x64 version. I'm Matthew. My new system contains a OEM ATI Radeon HD 6450 video card. It's a **HP Pavilion HPE-560z.** I would like to enable cards capabilities. I would like to request a little assistance in step by step how to make sure that I do it right. I have nothing against using official drivers. However, after speaking to a tech at ATI that the official driver package does not include a driver for this card yet for Linux or Windows. Thanks again for any assistance. 

Below is a link to the hardware specs on my system.

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02682447&tmp_track_link=ot_faqs/top_issues/en_us/c02682447/loc:3&lc=en&dlc=en&cc=us&#9001;=en&product=5061000&key=null&site=null]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02682447&tmp_track_link=ot_faqs/top_issues/en_us/c02682447/loc:3&lc=en&dlc=en&cc=us&lang=en&product=5061000&key=null&site=null")

---

### Post by wolfen69 on 2011-03-31
[This]("http://lotphelp.com/lotp/install-ati-catalyst-slackware-linux-2") individual was able to get that card working. Although written for Slackware Linux, the same principles should apply.

---

### Post by imaginedtruth on 2011-03-31
Thanks. I'll give it a try.

---

### Post by imaginedtruth on 2011-04-01
I looked it up and it shows how to make a package for Slackware, but being a bit new with Linux, I'm not sure how to adapt those instructions to work with Ubuntu. Any suggestions?

---

### Post by misterbiskits on 2011-04-01
visit AMD, 
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

1: desktop graphics
2: radeon hd series
3: radeon hd 6xxx series pcie
4: linux x86_64

if the above are your system specs, a driver exists.  (Is it a pcie card?)
Install it manually from a fresh ubuntu install. (in my experience trying system>preferences>hardware drivers will only screw it up)
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually]("http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually")
You might need to change the copypasta to reflect AMD's update to the 11.3 catalyst driver.

---

