---
title: "Wireless card won't work (kubuntu 7.10)"
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by TriMenToR on 2008-04-08
On my HP Pavilion DV6350eu I have a problem: my wireless card doesn't work. The led stays orange. I read several tutorials. I started with this one: [http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu) -710/ because "lspci | less" is telling me this: 03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
I followed this tutorial without getting errors, but my wireless still doesn't work. I also tried this one: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc)

The output of lspci -n | grep '14e4:43' is 03:00.0 0280: 14e4:4311 (rev 01) so I tried step 2b  (sp33008 Driver Download/Extraction). I ran cabextract sp33008.exe and got this output:

sp33008.exe: library not compiled to support large files.
sp33008.exe: library not compiled to support large files.
sp33008.exe: no valid cabinets found

All done, errors in processing 1 file(s)

Neither [http://ubuntuforums.org/showpost.php?p=3767216&postcount=273](http://ubuntuforums.org/showpost.php?p=3767216&postcount=273) and step 2a (sp34152 Driver Download/Extraction) worked. The output of cabextract sp34152.exe was:

sp34152.exe: library not compiled to support large files.
sp34152.exe: library not compiled to support large files.
Extracting cabinet: sp34152.exe
  extracting bcm1xsup.dll
  extracting bcm43xx.cat
  extracting bcm43xx64.cat
  extracting Bcmnpf64.sys
  extracting bcmwl5.inf
  extracting bcmwl5.sys
  extracting bcmwl564.sys
  extracting bcmwliss.dll
  extracting bcmwlnpf.sys
  extracting bcmwlpkt.dll
  extracting bcmwls.ini
  extracting bcmwls32.exe
  extracting bcmwls64.exe
  extracting bcmwlu00.exe
  extracting data1.cab
  extracting data1.hdr
  extracting data2.cab
  extracting ikernel.ex_
  extracting is.exe
  extracting launcher.ini
  extracting layout.bin
  extracting setup.exe
  extracting Setup.ini
  extracting setup.inx
  extracting setup.iss
  extracting sp34152.cva

All done, no errors.

Can anyone please help me? It's urgent :s

---

### Post by Glaxed on 2008-04-08
Look into ndiswrapper.

---

### Post by kevdog on 2008-04-08
Keep following the second tutorial you link to.  You need to install ndiswrapper and put the bcmwl5 driver inside ndiswrapper.

---

