---
title: "Ubuntu not booting off of live CD"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by garth813 on 2011-04-16
Hey everybody, I know that this question has been asked a few times but none of the previous answers have really helped me.  My question is about installing Linux from a live CD.  My desktop is running Windows XP (which is really messed up) and the computer is a Compaq Pesario.  Each time I try to boot from the disk I get to the Ubuntu menu, which asks if I want to try without installing, or install ect.  I want to completely override Windows so I was planning on installing and then repartitioning the disk to be fully Linux but each time I select the install option the CD just spins and spins.  Meanwhile the monitor is completely black and nothing appears to be happening.  I am using a disk I purchased from Ubuntu so I know my disk is not a problem (it is Ubuntu 10.10).  I also reconfigured the BIOS boot settings so that the CD drive would boot first.  Any help would be greatly appreciated.  Thanks.

---

### Post by Rubi1200 on 2011-04-16
Hi and welcome to the forums :-)

What graphics card do you have and how much RAM?

---

### Post by oklokl on 2011-04-16
First boot IDE

You setting Bios hdd ->Ubuntu-> not booting save.. (&#50864;&#48516;&#53804;&#45716; &#49324;&#50857;&#51088;&#44032; bios&#47196; &#49440;&#53469; &#54620; &#52395;&#48264;&#51704; &#54616;&#46300;&#47484; &#48176;&#51228; &#54616;&#44256; &#47924;&#51201;&#44148; IDE&#47484; &#52395;&#48264;&#51704;&#47196; &#51105;&#45716; &#50724;&#47448;&#47484; &#48156;&#49373; &#54633;&#45768;&#45796; &#44536;&#47111;&#44592; &#46412;&#47928;&#50640; &#49688;&#46041;&#51004;&#47196; &#54028;&#54000;&#49496;&#51012; &#54200;&#51665; &#54644;&#50556; &#54633;&#45768;&#45796;)
Only IDE boot.. setting.. auto Mode(Programs
No user-selectable
Therefore,

Manual edit Partition production (&#49688;&#46041;&#51004;&#47196; &#54028;&#54000;&#49496;&#51012; &#47564;&#46308;&#44256; )
sata boot setting.. (&#49324;&#53440; &#54616;&#46300;&#47484; &#49688;&#46041;&#51004;&#47196; &#49440;&#53469; &#54644;&#51452;&#49464;&#50836;..)
You setting sata booting setup

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=189191&stc=1&d=1302944957[/IMG]

---

### Post by garth813 on 2011-04-16
Hey thanks for the reply, apparently I have 446 MB of RAM which to me seems pretty low, and the Graphics card reads under the DirectX Diagnostic Tool:Name NVIDIA GeForce 6150 LE
Manufacturer: NVDIA
Chip Type GeForce 6150 LE
Approx. Total Memory 256.MB
Maybe my system is inadequate for tUbuntu, or maybe I have to delete alot of things?

---

### Post by Rubi1200 on 2011-04-16
See here for more information on minimum system requirements:
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

But, that is only a rough guide. I know people who have installed and run Ubuntu on 512MB of RAM.

I do think you might need to try setting nomodeset at boot for your video card. See here for more details:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

---

