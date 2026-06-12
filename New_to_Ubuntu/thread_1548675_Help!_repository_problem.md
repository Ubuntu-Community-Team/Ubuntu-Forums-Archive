---
title: "Help! repository problem"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by Velenjak on 2010-08-08
hello, i recently installed 10.04 through wubi and im facing some problems.... im trying to download the latest version of qtstalker (.36) and the repositories are only showing version .32..... i had ubuntu exclusively  for a year and i ran qtstalker .36 with no problems. 

initially, i assumed that my computer wasnt getting the most recent updates - when i tried to find a download server i would get the error message of "no suitable server found"  - i then connected my computer directly (not thru router) and i was able to find a suitable server. this did not fix my problem though...

still through the software center and synaptic the only versions available are .32..... am i missing some sort of update? please help!!

---

### Post by beew on 2010-08-08
You never get the latest versions in the Ubuntu repositories. You get a patched version which has greater stability and integrates better into the system but it is never the most updated version. Ubuntu does not update its softwares in the repositories between releases except for security updates, so if you want the latest version  you should either download it from the vendor's website or add a third party PPA to your program source list (if this option is available)

---

### Post by tcopeland on 2010-08-08
The version .36 is most likely not yet in the Ubuntu repositories. You can download the tar.gz from [this link]("http://downloads.sourceforge.net/project/qtstalker/qtstalker/qtstalker-0.36/qtstalker-0.36.tar.gz?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fqtstalker%2Ffiles%2F&ts=1281305951&mirror=superb-sea2").

---

### Post by Velenjak on 2010-08-08
this is kinda weird... i installed qtstalker .36 (about a year ago) through synaptic and found all the packages i needed... 


im looking at the folder - how do i install this program? i looked at the installation sheet and im not understanding it all..... thanks for the replies

---

### Post by Velenjak on 2010-08-08
now im getting .36 documentation in the synaptic..... - i cant figure out how to launch the .36 folder - i see no executable files...

---

### Post by Velenjak on 2010-08-08
ok so im making a little progress.... found this article...
[http://www.zwets.com/ta-lib/](http://www.zwets.com/ta-lib/)

when i input the first line [deb [http://www.zwets.com/debs](http://www.zwets.com/debs) unstable/]  into my /etc/apt/source i get the error 
no public key available

... this is way over my head... help is much appreciated

---

