---
title: "Black screen after ATI Driver install"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by hoxzyk on 2011-06-01
Hello,

Having issues...........!!!!

Lappy:  HP dv6-3006tx
   
  I am having an issue installing the ATI Driver for the laptop via the Hardware Driver Manager in ubuntu…..
   
  When I click “Activate” it will download and seems to install fine, no errors!!! Then asks to reboot for the update to finish….
   
  When I reboot it will just hang on a black screen and do nothing. 
  Then I just reinstall Ubuntu again and try again….
   
  This is using either Ubuntu 10.4 or 11.4 both have the same issues.
   
  Has anyone had this issue before and fixed it?
   
  Happy Regards,
  Ryan

---

### Post by alphacrucis2 on 2011-06-01
> **hoxzyk said:**
> Hello,

Having issues...........!!!!

Lappy:  HP dv6-3006tx
   
  I am having an issue installing the ATI Driver for the laptop via the Hardware Driver Manager in ubuntu&#8230;..
   
  When I click &#8220;Activate&#8221; it will download and seems to install fine, no errors!!! Then asks to reboot for the update to finish&#8230;.
   
  When I reboot it will just hang on a black screen and do nothing. 
  Then I just reinstall Ubuntu again and try again&#8230;.
   
  This is using either Ubuntu 10.4 or 11.4 both have the same issues.
   
  Has anyone had this issue before and fixed it?
   
  Happy Regards,
  Ryan

Assuming you have installed the Catalyst driver and have got to the black screen, forcibly reboot via power reset. Then hold down the Shift key when GRUB boots to make it display the menu. Select the recovery mode line and hit enter. It will eventually display the recovery menu. Arrow down the menu and select either netroot or root. Hit enter. When it displays the command prompt, try the following:

```
aticonfig --initial -f
```

or after installing via the Hardware Driver manager make sure you enter the above command prefixed by sudo before rebooting. The -f flag means "force".

Then 

```
shutdown -r now
```

Let it boot normally this time. If it works then good otherwise repeat the above process but instead of the aticonfig command you can get rid of the Catalyst driver via:

```
apt-get remove --purge fglrx*
```

Then a reboot should get you back to square 1. From there you will need to let us know which particular ATI graphics card you have via lspci,

---

### Post by hoxzyk on 2011-06-01
Thanks i will test this out when i get home!!!

Im pretty sure the graphics card is a ATI Radeon HD5650, but ill supply the information you requested asap!!!!

---

### Post by alphacrucis2 on 2011-06-01
> **hoxzyk said:**
> Thanks i will test this out when i get home!!!

Im pretty sure the graphics card is a ATI Radeon HD5650, but ill supply the information you requested asap!!!!


If you can't get the Catalyst driver from the ubuntu repos to work, you could try the latest linux 32 or 64 bit Catalyst driver, which you can download from AMD's website. To install the driver AMD provide, you are best to install it via the buildpkg method as described on the Ubuntu Binary Driver Howto - ATI

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

The article pertains to Catalyst 11.2 and Ubuntu Maveric (10.10) but it will still serve as a guide for Catalyst 11.5 (the current version) and either lucid or natty, altering the instructions as appropriate.

---

### Post by hoxzyk on 2011-06-01
Ok well pretty much the problem now after selecting recovery is it also hangs on a black screen...... would just reinstalling ubuntu again do the same thing then just move on to next step which is supplying the GPU details? or installing via ATI web page..?

---

### Post by alphacrucis2 on 2011-06-01
> **hoxzyk said:**
> Ok well pretty much the problem now after selecting recovery is it also hangs on a black screen...... would just reinstalling ubuntu again do the same thing then just move on to next step which is supplying the GPU details? or installing via ATI web page..?

If you still get a black screen after selecting the recovery mode grub menu line then there the catalyst driver is not likely to be the problem as it shouldn't even be getting loaded when you select recovery mode. Can you not get into the root prompt at all?

---

### Post by hoxzyk on 2011-06-01
Well currently i just reinstalled it and following the guide to install the driver from ATI web site.... see how that works...


Well it did not for me... just showed some text then went black and hanged.... Unsure exactly what the command is to bring up the command like but i tried ctrl + alt + f1 -> f7......... but i might be completely wrong heh..... well im not sure what it is due to but... no image after that driver is installed.... tried an external monitor, still does not display... while its a black screen i can push Ctrl + Alt + Del and that will reboot the lappy.... so i guess its not booting into the os at all.... not sure what you call it but i think it hangs after Grub?

---

### Post by hoxzyk on 2011-06-01
..... now with the guide you sent i get up to where i create the 4 packages on my desktop then run 

sudo dpkg -i *.deb

I receive

Errors were encounterd while processing: 
fglrx
fglrx-amdcccle
fglrx-dev

I also tried fixing the broken packages and same error.....

---

### Post by hoxzyk on 2011-06-01
OMG DUDE!!! i love you!!!! never mind about what i said i could install the packages via Synaptic package manager which did not bring up errors!!!

Thanks heaps for the help and the guides!!!! unsure why i found this sooo hard to me sounded like a simple task but i wasted sooo much time on it!!!! thanks heaps again!!!!

---

### Post by alphacrucis2 on 2011-06-01
> **hoxzyk said:**
> OMG DUDE!!! i love you!!!! never mind about what i said i could install the packages via Synaptic package manager which did not bring up errors!!!

Thanks heaps for the help and the guides!!!! unsure why i found this sooo hard to me sounded like a simple task but i wasted sooo much time on it!!!! thanks heaps again!!!!

Glad to be of help. AMD/ATI release an update every month and there are often significant improvements especially for the newer ATI cards but Ubuntu play it fairly conservative with the Catalyst driver in their repos. A good place to look is on the Phoronix forums. One of their forums is dedicated to the ATI Linux proprietary driver. People post reports of how they got on installing the latest linux version when it gets released. It's a good idea to check there to see if anyone had any problems with the latest release before you update yourself. I already knew Cat 11.5 was pretty good as it has been out for a couple of weeeks and I installed it myself without problems.

PS. I've no idea what problem dpkg was having installing the four fglrx deb files. Sounds like something had got a broken. Appears that the Synaptic Package manager was able to sort it out. Phew.

---

### Post by amajewicz on 2012-06-26
> **alphacrucis2 said:**
> If you still get a black screen after selecting the recovery mode grub menu line then there the catalyst driver is not likely to be the problem as it shouldn't even be getting loaded when you select recovery mode. Can you not get into the root prompt at all?

Okay - this is exactly the problem I'm having. Black screen in recovery mode and I can't figure out how to get the root prompt. Any ideas? Sorry about this being an old post. 

Thanks!

---

