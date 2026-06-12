---
title: "XP not listed on Grub list"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by nick24 on 2009-09-03
Tonight I installed Ubuntu 9.04 alongside XP hoping to dual boot. XP was using the whole HD before I resize it in half for ubuntu, everything went well and I can boot to ubuntu but not to XP, XP is not in the list. My menu.lst is empty.......nothing is on there, it's blank. Please help.

---

### Post by kansasnoob on 2009-09-03
Go to terminal and run:

```
sudo fdisk -l
```

(Lower case L at the end!)

Post the output here please.

---

### Post by nick24 on 2009-09-03
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe0d5e0d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19333   155292291    7  HPFS/NTFS
/dev/sda2           19334       38913   157276350    5  Extended
/dev/sda5           19334       38164   151259976   83  Linux
/dev/sda6           38165       38913     6016311   82  Linux swap / Solaris


thank you for your reply and help

---

### Post by kansasnoob on 2009-09-03
Looks OK so far. Post the output of:

```
cat /boot/grub/menu.lst
```

---

### Post by df6269 on 2009-09-03
Please try to modify grub for windows in [COLOR="Red"]/etc/default/grub[/COLOR]

---

### Post by nick24 on 2009-09-03
cat: /boot/grub/menu.lst: No such file or directory

---

### Post by nick24 on 2009-09-03
> **df6269 said:**
> Please try to modify grub for windows in [COLOR="Red"]/etc/default/grub[/COLOR]

I wish I knew how to do that, please explain more. Thanks

---

### Post by kansasnoob on 2009-09-03
> **nick24 said:**
> cat: /boot/grub/menu.lst: No such file or directory

cat**:** /boot/grub/menu.lst

your command was wrong! Copy and paste:

```
cat /boot/grub/menu.lst
```

---

### Post by kansasnoob on 2009-09-03
> **df6269 said:**
> Please try to modify grub for windows in [COLOR="Red"]/etc/default/grub[/COLOR]

According to the OP this is 9.04 not 9.10!

---

### Post by nick24 on 2009-09-03
> **kansasnoob said:**
> cat**:** /boot/grub/menu.lst

your command was wrong! Copy and paste:

```
cat /boot/grub/menu.lst
```



It still gives me the same error. I copied and pasted it. I even went to grub directory and menu.lst was not there. here is the output after the copying and pasting your command. 



:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory


Thanks for your prompt reply.

---

### Post by kansasnoob on 2009-09-03
> **nick24 said:**
> It still gives me the same error. I copied and pasted it. I even went to grub directory and menu.lst was not there. here is the output after the copying and pasting your command. 



:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory


Thanks for your prompt reply.

OK, the first time you added a ":" like this:

"cat: /boot/grub/menu.lst"

This time you turned the lower case L at the end into a 1 "one" I think.

It must be right, copy and paste:

```
cat /boot/grub/menu.lst
```

---

### Post by kansasnoob on 2009-09-03
If we're still having problems post the ouput of:

```
grub-install -v
```

---

### Post by nick24 on 2009-09-03
niko@niko-laptop:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
niko@niko-laptop:~$ 


This time I'm copying and pasting the command and output together so you can see it better. I don't think I have such a directory. I don't know if that's possible though. Thanks again for your help.

---

### Post by nick24 on 2009-09-03
> **kansasnoob said:**
> If we're still having problems post the ouput of:

```
grub-install -v
```


grub-install (GNU GRUB 1.96)

---

### Post by kansasnoob on 2009-09-03
> **nick24 said:**
> grub-install (GNU GRUB 1.96)

OK, that's GRUB_2 which is not native to 9.04 but only to Karmic!

Anyway it's like comparing apples to oranges!

At the command line run:

```
sudo update-grub2
```

If it still fails maybe the menu is just hidden.

Look here:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I'm still figuring that out myself.

---

### Post by kansasnoob on 2009-09-03
> **df6269 said:**
> Please try to modify grub for windows in [COLOR="Red"]/etc/default/grub[/COLOR]

My bad, you were right, it's GRUB_2!

---

### Post by nick24 on 2009-09-03
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-4-generic
Found initrd image: /boot/initrd.img-2.6.31-4-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done


This is the output, I will reboot and update you what happens. Thanks again.

---

### Post by nick24 on 2009-09-03
Thanks a lot for your patience and help. It worked. I logged in to XP and Ubuntu just to make sure. You rock! :D

---

### Post by kansasnoob on 2009-09-03
> **nick24 said:**
> Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-4-generic
Found initrd image: /boot/initrd.img-2.6.31-4-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done


This is the output, I will reboot and update you what happens. Thanks again.

No problem, but I'd also recommend running:

```
cat /etc/issue
```

And if it shows, "Ubuntu karmic (development branch)", please click on the "report post" button and ask that this be moved to Karmic testing.

You'll get better support there .......... maybe:)

---

### Post by kansasnoob on 2009-09-03
> **nick24 said:**
> Thanks a lot for your patience and help. It worked. I logged in to XP and Ubuntu just to make sure. You rock! :D

Sorry for the confusion, in just a couple of weeks the first question to ask about boot problems will be, "post the output of grub-install -v".

Such is life:D

---

### Post by nick24 on 2009-09-03
Yup you are right it does say 'Ubuntu karmic (development branch)'. I will do that.

---

### Post by kansasnoob on 2009-09-03
> **nick24 said:**
> Yup you are right it does say 'Ubuntu karmic (development branch)'. I will do that.

It's all good, but you did mistakenly say you'd installed 9.04 when in fact you'd installed 9.10.

I personally don't like the new GRUB but I know it's here to stay.

Hell, I loved Win ME:D

---

