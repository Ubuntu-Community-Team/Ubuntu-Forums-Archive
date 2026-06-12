---
title: "Dual boot Ubuntu 9.10 blank screen"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by anand_30 on 2010-01-09
I was ignoring this problem as it is not very annoying.But here it is:-

I have dual boot Ubuntu 9.10 (complete install not Wubi installation:-10Gb of my 40Gb HD)and Windows xp(Ubuntu installed after Windows).When I turn on my computer and select ubuntu 9.10 I get ubuntu icon then blank screen showing blinking cursur at left then screen goes blank and nothing comes.To get into ubuntu I need restart then I have to select Windows xp.After getting into xp. I again restart from xp then I select ubuntu 9.10.This time it works perfectly without any blank screen.

So I have to follow the procedure of getting into windows>>restart>>ubuntu to successfully boot into ubuntu.I am complete new to ubuntu so I have not tried recovery mode ,mem test.Is there any way to get rid of this restarting to get into ubuntu?

I purchased my computer back in 2005(very old I know).
My system specs Intel pentium 4 CPU 2.40GHz,1.25 Gb of RAM.
GNU Grub version 1.97~beta 4.

(Just stating that the problem is there only when I turn off and then turn on,and not for subsequent restarts.) 
I thanks in advance and very much grateful to this community and helpers.

---

### Post by gsmanners on 2010-01-09
Modern motherboards don't tend to last much more than 2 or 3 years, so I wouldn't be surprised if it was about to go dead on you. The other thing is the power supply, which can be problematic, although those generally last a little longer on average.

It's not an old computer, I think. The CPU and the RAM are still okay, more than likely.

---

### Post by kansasnoob on 2010-01-09
> **anand_30 said:**
> I was ignoring this problem as it is not very annoying.But here it is:-

I have dual boot Ubuntu 9.10 (complete install not Wubi installation:-10Gb of my 40Gb HD)and Windows xp(Ubuntu installed after Windows).When I turn on my computer and select ubuntu 9.10 I get ubuntu icon then blank screen showing blinking cursur at left then screen goes blank and nothing comes.To get into ubuntu I need restart then I have to select Windows xp.After getting into xp. I again restart from xp then I select ubuntu 9.10.This time it works perfectly without any blank screen.

So I have to follow the procedure of getting into windows>>restart>>ubuntu to successfully boot into ubuntu.I am complete new to ubuntu so I have not tried recovery mode ,mem test.Is there any way to get rid of this restarting to get into ubuntu?

I purchased my computer back in 2005(very old I know).
My system specs Intel pentium 4 CPU 2.40GHz,1.25 Gb of RAM.
GNU Grub version 1.97~beta 4.

(Just stating that the problem is there only when I turn off and then turn on,and not for subsequent restarts.) 
I thanks in advance and very much grateful to this community and helpers.

I would like to see the output of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

I rather prefer having the results.TXT compressed as a tar.gz and then attached using the paper clip at the top of this form, but feel free to attach however is best for you.

BTW could you provide more specific system info? Actual computer brand, etc? It may be helpful.

---

### Post by anand_30 on 2010-01-09
> **kansasnoob said:**
> I would like to see the output of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

I rather prefer having the results.TXT compressed as a tar.gz and then attached using the paper clip at the top of this form, but feel free to attach however is best for you.

BTW could you provide more specific system info? Actual computer brand, etc? It may be helpful.

Thank you for your reply.:D
I have attached RESULT.TXT.tar.gz
I have assembled desktop.
Sorry I don't know the brand of motherboard(sounds stupid)I have lost that papers but most probably as I remember its mercury motherboard(don't know which type sorry!).

---

### Post by kansasnoob on 2010-01-10
Sorry to be so slow. I'll take a look at this right now.

---

### Post by kansasnoob on 2010-01-10
Well I see nothing actually wrong there. I have encountered some situations where grub2 just refuses to play well, particularly on some Toshiba laptops.

A couple of recent examples:

[http://ubuntuforums.org/showthread.php?t=1373782](http://ubuntuforums.org/showthread.php?t=1373782)

[http://ubuntuforums.org/showthread.php?t=1375460](http://ubuntuforums.org/showthread.php?t=1375460)

[http://ubuntuforums.org/showthread.php?t=1373378](http://ubuntuforums.org/showthread.php?t=1373378)

There are many, many more. Meierfra, who wrote that Boot Info Script, had this to say yesterday:

> I think strange cases like this one are due to a miscommunication between Grub 2 and the Bios. (in other words, I have no clue what is going on)

[http://ubuntuforums.org/showpost.php?p=8639043&postcount=24](http://ubuntuforums.org/showpost.php?p=8639043&postcount=24)

So, in my opinion, it would be well worth trying to revert to legacy grub. I wrote a HowTo:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

I do however plan on making a few minor tweaks to that as soon as I'm done reviewing and replying to yesterdays threads.

This is the general idea:

[http://ubuntuforums.org/showpost.php?p=8637867&postcount=20](http://ubuntuforums.org/showpost.php?p=8637867&postcount=20)

Of course that was written specifically for them, but I see great similarities.

The only real difference is that they first had to restore the grub bootloader which you do not, just boot into Ubuntu as you have been.

And their Ubuntu was on sda5 whereas yours is on sda7, so where I told them to set grub root to (hd0,4) you'd need to set root to (hd0,6) like this:

> Now we need a grub shell:

```
sudo grub
```

```
root (hd0,6)
```

```
setup (hd0)
```

You should see this:

[QUOTE]Checking if "/boot/grub/stage1" exists... **yes**
Checking if "/boot/grub/stage2" exists... **yes**
Checking if "/boot/grub/e2fs_stage1_5" exists... **yes**
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...* 15 sectors are embedded.
**succeeded**
Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage
2 /boot/grub/menu.lst"... **succeeded**
Done.
Without the three yes and two succeeded responses something is wrong and you'll likely be unable to boot! If all looked right just run:

```
quit
```
[/QUOTE]
Even the steps for adding Windows are identical as you both have Windows on sda1.

Depending on your level of technical knowledge I'd be glad to retype instructions 100% specific for your system if that would make you more comfortable.

Feel free to send me a brief PM pointing me back to this thread if you have questions or if you'd prefer that I type you some system specific instructions.

Always best to plan ahead, so feel free to ask questions.

---

### Post by anand_30 on 2010-01-10
> **kansasnoob said:**
> 
Sorry to be so slow.

No 'sorry' Kansasnoob you are helping me I should be grateful to you.

> **kansasnoob said:**
> 
Of course that was written specifically for them, but I see great similarities.

The only real difference is that they first had to restore the grub bootloader which you do not, just boot into Ubuntu as you have been.

And their Ubuntu was on sda5 whereas yours is on sda7, so where I told them to set grub root to (hd0,4) you'd need to set root to (hd0,6) like this:


Even the steps for adding Windows are identical as you both have Windows on sda1.

Depending on your level of technical knowledge I'd be glad to retype instructions 100% specific for your system if that would make you more comfortable.

Feel free to send me a brief PM pointing me back to this thread if you have questions or if you'd prefer that I type you some system specific instructions.

Always best to plan ahead, so feel free to ask questions.

I removed grub2 and installed grub.
I have performed following things
sudo grub

grub> root (hd0,6)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

Am I doing wrong?

---

### Post by anand_30 on 2010-01-11
Oh yes I was doing wrong.

I forgot to execute command
sudo grub-install /dev/sdaNow I have performed the instructions perfectly and have Legacy grub. 

My problem is partly solved now because I can enter into ubuntu without restarting and seeing face of windows by Grub loading>>Esc>>ubuntu 9.10>>Enter  but I can't enter into ubuntu without pressing Esc and selecting ubuntu from list.In that case its same problem of blank screen.

Thank you Kansasnoob for helping me.:smile:It will be great help it you can tell me how to get rid of default booting into ubuntu by grub i.e. I don't want the message "Grub loading press 'Esc' to enter in boot menu" instead I want boot menu directly.

---

