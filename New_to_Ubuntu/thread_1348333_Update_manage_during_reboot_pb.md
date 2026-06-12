---
title: "Update manage during reboot pb"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by fchartier on 2009-12-07
Hi all, 

I have juste ubuntu 9.10 and and downloaded all the sofware listed in Update manager = 90mb

a) Once finished install, I rebooted, selected ubuntu and before the ubuntu loading window, a dark window appeared with commands. **grub (i am not 100% sure how u spell it) **showing ( ''Press TAB for command list etc''.. which i did as i thought that it was part of the update process. There is a list of commands separated by spaces. Unfortunately i do not know how to get pass this point. the only command i was able to type: reboot.

  b) Just so you know how i installed which could part of the reason of this bug or not. I used wubi and seen as the normal way of letting wubi install the iso. which i did a couple of times. i managed to follow some tips on the forum saying to download the iso file for ubuntu directly, placing the file in  the same folder as wubi, then executing wubi. It all worked !! it was a great relief. Now i am a bit stuck. 

c) Other question, it seems that my laptop is a bit slow on ram, 500 mb, processor 1.7 ghz. when i installed ubuntu i used 17 gb, (33 were free on my C = 55 in total). Should i reinstall ubuntu (the same way) using more size for better conditions of use? 

If you know anything about this, THanks a lot.

Cheers

---

### Post by cariboo on 2009-12-11
It seems your update didn't complete. From the grub menu, choose an older kernel and boot from that. Once at the desktop open an Applications-->Accessories-->Terminal and type:

```
sudo apt-get -f install
```

The above command will install any missing packages. Once done, you should be able to boot with your new kernel.

---

