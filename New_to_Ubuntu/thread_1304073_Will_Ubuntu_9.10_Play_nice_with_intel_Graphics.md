---
title: "Will Ubuntu 9.10 Play nice with intel Graphics?"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by nakama85 on 2009-10-28
I only ask because I had so many issues with graphics speed on 9.04 I had to downgrade. Should 9.10 have the issues corrected.

---

### Post by Jazzy_Jeff on 2009-10-28
I believe intel graphics run great in the new release from what I have read.

---

### Post by nakama85 on 2009-10-28
> **Jazzy_Jeff said:**
> I believe intel graphics run great in the new release from what I have read.

awesome I will have to give it a shot.

I am thinking of dual booting via a second HDD to test it out so that I don't have to go through such a headache if it does not work out

---

### Post by Gazneth on 2009-10-28
My wife currently uses 9.10 netbook remix on an Acer Aspire and it performs much better than under 9.04. She has used it since a late Alpha version. All of the previous graphic lag, screen tearing and sloooow scrolling are gone.

---

### Post by nakama85 on 2009-10-28
> **Gazneth said:**
> My wife currently uses 9.10 netbook remix on an Acer Aspire and it performs much better than under 9.04. She has used it since a late Alpha version. All of the previous graphic lag, screen tearing and sloooow scrolling are gone.

yyyyyyeeeeeeessssssss!!!!!!!!!!:guitar:

---

### Post by hockeyfighter09 on 2009-10-28
Here is some info on the new intel graphics in 9.10 from the Ubuntu website.

"The Intel video driver has switched from the "EXA" acceleration method to the new "UXA", solving major performance problems of Ubuntu 9.04. Ubuntu 9.10 RC also features kernel mode setting by default on Intel hardware, which reduces boot-time flickering and dramatically speeds up suspend/resume."

---

### Post by NoFearDJB on 2009-10-28
> **nakama85 said:**
> I only ask because I had so many issues with graphics speed on 9.04 I had to downgrade. Should 9.10 have the issues corrected.

On my Acer Aspire One with Intel graphics, I can run compiz effects! WOOT! =) 
I think it has vastly improved! :biggrin:

---

### Post by Aearenda on 2009-10-28
Brilliant on my Intel 945. Not so good if you need the Poulsbo driver (Intel GMA500), rather than the standard intel one. See [this thread]("http://ubuntuforums.org/showthread.php?t=1229345").

---

### Post by j7%&lt;RmUg on 2009-10-28
Its looking good for me then, hopefully i should rid myself of that compiz lag iv had since 8.10, might finally be able to work with graphics better too.

---

### Post by immerohnegott on 2009-10-29
Just tossing in my two cents here.

Performance-wise, the graphics seem to run just fine for me on a GMAx4500MHD. No issues with compiz at all.

As far as image quality is concerned, there is still no dithering for 6-bit LCD panels, which means the horrific banding of gradients remains if you're on a cheaper LCD display (e.g. most laptops).

Just checked it on my CRT and it looks wonderful, so this is definitely localized to the jank-panel segment. Coincidentally, dual-head works well - even had full compiz running across both displays.

---

### Post by morrow on 2009-10-30
Although it's nice to see some headway in the Intel department, I note that on my Intel X3100 performance is (subjectively, of course) below what 8.04 had to offer (Intel X3100).

Edit: Not by a large margin though. In compiz/metacity, this mostly manifests when scrolling across multiple virtual desktops where one or more of them contains packed windows (such as Firefox or MatLab).

---

### Post by ibizatunes on 2009-10-30
Yes Intel drivers are a lot better in 9.10, download it and give it a try!

---

### Post by scratman on 2009-10-30
I had problems with Intel Graphics when I updated.  When I booted up I couldn't get to a GUI Login.  Seems like my PC doesn't like version 185 of the graphics.  To resolve this, I booted into my previous kernel, selected Version 173 as default, and then booted back into 9.10.  Works a treat now.

---

### Post by Scunnered on 2009-10-30
I have been using 9.10 since the RC and it works a treat. No graphic problems.

Trust this assists

---

### Post by 3rdalbum on 2009-10-30
> **scratman said:**
> I had problems with Intel Graphics when I updated.  When I booted up I couldn't get to a GUI Login.  Seems like my PC doesn't like version 185 of the graphics.  To resolve this, I booted into my previous kernel, selected Version 173 as default, and then booted back into 9.10.  Works a treat now.

173 and 185 are Nvidia driver versions. If you're using Intel graphics, then you definitely don't want Nvidia drivers.

---

### Post by mag1 on 2009-10-30
Great news about not more video tearing and performance, does this also mean flash loaded sites will run faster now as that was also one major annoyance, or is that more a flash/firefox problem?

---

### Post by ben44b on 2010-04-09
I got excited after reading this thread that I would be able to turn on Compiz with my Brookdale Intel 8485G chipset. (I have never been able to use Compiz since I've used Ubuntu). 

Unfortunately, when I tried to change the desktop effects, it said it could not be enabled. 

Keep hope alive...

---

### Post by Xyphoid on 2010-04-09
> **mag1 said:**
> Great news about not more video tearing and performance, does this also mean flash loaded sites will run faster now as that was also one major annoyance, or is that more a flash/firefox problem?

I've been waiting since Intrepid and Jaunty for a better Flash plugin, but no such luck. I'm still in XP on my Acer because of that...

---

