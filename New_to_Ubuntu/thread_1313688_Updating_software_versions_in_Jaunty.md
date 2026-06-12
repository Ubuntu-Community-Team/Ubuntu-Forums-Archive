---
title: "Updating software versions in Jaunty"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by jfloydb on 2009-11-03
I noticed that 9.10 offers (in synaptic and the store) later versions of various software packages than 9.04 does in synaptic. How can I update to the latest version of any software in Jaunty? Specifically: I would like the latest versions of FBReader and BleachBit. Thanks...

---

### Post by LarsW_Tierp on 2009-11-03
You can try to go diretcly to the softwares homepage and look for downloads.
example: [FBreader]("http://www.fbreader.org/desktop/debian.php")

---

### Post by LarsW_Tierp on 2009-11-03
And [URL="http://sourceforge.net/projects/bleachbit/files/bleachbit/bleachbit_0.7.0-1_all_ubuntu904.deb/download"]BleachBit
[/URL]

---

### Post by jfloydb on 2009-11-03
I did try going to the FBReader site, but I could not figure out what I had to do to get a version update. I was humbly hoping that someone could give me some type of "sudo apt-get/update" [sic] command for getting version updates. Thanks.

---

### Post by LarsW_Tierp on 2009-11-03
**Installation from the repository:** 	
[LIST]
[*]add the following lines to your /etc/apt/sources.list: 		
deb [http://www.fbreader.org/desktop/debian](http://www.fbreader.org/desktop/debian) stable main 		
deb-src [http://www.fbreader.org/desktop/debian](http://www.fbreader.org/desktop/debian) stable main
[*](optional) install our PGP key:
[LIST]
[*]download [the key file]("http://www.fbreader.org/desktop/debian/geometer.fbreader.org.asc")
[*]as root, run ‘apt-key add geometer.fbreader.org.asc’
[/LIST]
[*]as root, run ‘apt-get update’.
[*](optional) by default, gtk+ interface module will be installed. If you prefer to use FBReader with qt (or with qt4) inreface, run with root privileges ‘apt-get install libzlui-qt’ (or ‘apt-get install libzlui-qt4’).
[*]as root, run ‘apt-get install fbreader’.
[/LIST]

---

### Post by jfloydb on 2009-11-03
Thanks LarsW_Tierp, the BleachBit link downloaded the package and I installed it. Thank you very much. 

However, I still cannot (yet) figure out how up date FBReader...

---

### Post by jfloydb on 2009-11-04
> **LarsW_Tierp said:**
> **Installation from the repository:** 	
[LIST]
[*]add the following lines to your /etc/apt/sources.list: 		
deb [http://www.fbreader.org/desktop/debian](http://www.fbreader.org/desktop/debian) stable main 		
deb-src [http://www.fbreader.org/desktop/debian](http://www.fbreader.org/desktop/debian) stable main
[*](optional) install our PGP key:
[LIST]
[*]download [the key file]("http://www.fbreader.org/desktop/debian/geometer.fbreader.org.asc")
[*]as root, run &#8216;apt-key add geometer.fbreader.org.asc&#8217;
[/LIST]
[*]as root, run &#8216;apt-get update&#8217;.
[*](optional) by default, gtk+ interface module will be installed. If you prefer to use FBReader with qt (or with qt4) inreface, run with root privileges &#8216;apt-get install libzlui-qt&#8217; (or &#8216;apt-get install libzlui-qt4&#8217;).
[*]as root, run &#8216;apt-get install fbreader&#8217;.
[/LIST]

I couldn't add lines to /etc/apt/sources.list. I didn't have permission. And I don't know how to do anything as root.

Thanks for all your help...

---

