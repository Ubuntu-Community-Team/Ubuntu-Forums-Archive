---
title: "converting dmg to iso using iat"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by iansane on 2011-07-11
Hi,

I've been at it for a few hours now trying to convert a dmg file so I can mount it. I've tried mounting the dmg directly, convert to img with dmg2img and then mount the img, basically tried everything I can find on the Internet about converting or mounting dmg files on Linux/Ubuntu.

Always the same error when mounting, hfs, hfsplus, udf, iso9960, always get the error about incorrect file system, or bad block.

I would assume the file is corrupt if it wasn't for the fact that every article I found about it people were having the same problems but none of them seemed to answer what the solution was.

So anyway, now I'm trying iat to convert directly to an iso

```
iat mac.dmg mac.iso
```

It hasn't given any errors and after a long time output
```
Detect Signature RAW 2 at 870193965
```
and it is still running. I'm not sure if that is an error or just some output I don't understand.

My harddrive light is flashing and I see iat in HTOP using 100% cpu on one core but no file has shown up on my desktop and no indication from terminal if it is actually working.

Has anyone used iat before and is it taking so long because it is a 7GB dmg file? It's been running for about an hour with no sign of life other than the hard drive light and cpu indicator.


I should add that when I check the file with the file command this is all I get 
```
lotus@lotus-master:~/Desktop$ file mac.dmg
mac.dmg: data
lotus@lotus-master:~/Desktop$
```


Thanks

---

### Post by dcsoldschool53 on 2011-07-11
Check this web page out, maybe it can help you.
[http://www.ehow.com/how_5847479_convert-dmg-iso-ubuntu.html](http://www.ehow.com/how_5847479_convert-dmg-iso-ubuntu.html)

---

### Post by iansane on 2011-07-12
> **dcsoldschool53 said:**
> Check this web page out, maybe it can help you.
[http://www.ehow.com/how_5847479_convert-dmg-iso-ubuntu.html](http://www.ehow.com/how_5847479_convert-dmg-iso-ubuntu.html)

I tried that method but something was going wrong in the conversion with dmg2iso making the file un-mountable. I switched over to my win7 partition(hangs head in shame) and downloaded dmg2img.exe and it converted the image correctly to an iso.

One thing I did differently though was to use the command

```
dmg2img mac.dmg mac.iso
```
instead of
```
dmg2img mac.dmg mac.img
```

So it converted it directly to an iso instead of img.

Looking at the dmg2img website there is actually a dmg2iso script for historical purposes that apparently was added into the dmg2img script. I'm going to try this method on Ubuntu and hopefully it works like it did on windows.

Thanks for the link to the how-to though. It is a easy read and straight forward. :-)

---

