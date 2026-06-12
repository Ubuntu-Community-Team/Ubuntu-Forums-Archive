---
title: "Change default OS in Grub2 and 9.10"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by SlappyPappy on 2009-10-31
My girlfriend is killing me, Ubuntu is the default OS and I need it to be Windows 7 for her.

I've looked in the forum and people are talking about it but I've yet to find an answer.

Thanks for any help.

:confused:

---

### Post by Schendje on 2009-10-31
Hi!

You can install Startup-Manager in the Software Center. Open it at System -> Admin -> Startup-Manager and change the setting under "Default operating system".

That should do the trick. Good luck!

//Edit: you might want to run "sudo update-grub" in a Terminal. I don't know if this is required, but just to be on the safe side.

---

### Post by SlappyPappy on 2009-10-31
Cool, thanks man. I'm going to check that out.

God I wish she would just get over it and use Ubuntu more.

Ubuntu, the chick unfriendly OS!  :D

---

### Post by drs305 on 2009-10-31
Click on the SUM link in my signature line for a guide on using StartUp-Manager. It is an excellent tool in Grub, and is able to do some of it's tweaks in the new Grub 2.

If you prefer to change it via file editing, open /etc/default/grub and look for the "DEFAULT=0" line.
Open a terminal and type: 
```
grep menuentry /boot/grub/grub.cfg
```
Count the "menuentry" listings, starting with 0. Note the Windows line. If it's the fourth line, it would be "DEFAULT=3".
Save /etc/default/grub and then run:
```
sudo update-grub
```

---

### Post by SlappyPappy on 2009-11-01
Thank guys, I tried both ways and they both work.

I also changed it from 10 to 5 seconds for startup.

Very happy and now no more complaints from the girlfriend.

Rock on with your bad grub self! :guitar::guitar::guitar:

---

### Post by firesock on 2010-09-11
Thank you very much!

---

### Post by pHr34kY on 2010-11-02
I found a different way of doing this in 10.10 Maverick:

If you look in /etc/grub.d/ you'll see the files which create the grub OS ordering.

```

00_header        
05_debian_theme
10_linux
20_linux_xen
20_memtest86+
30_os-prober
40_custom
41_custom

```

You'll see that other OSes are probed AFTER linux. A quick file rename changes that:

```

sudo mv /etc/grub.d/30_os-prober /etc/grub.d/05_os-prober
sudo update-grub

```

You'll see this:

```

Generating grub.cfg ...
Found Microsoft Windows XP Professional on /dev/sda1
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

Note that windows is now first.

---

