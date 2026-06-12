---
title: "Need help to get to the GUI"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by arghyaghosh on 2010-11-13
Hi All ,

I am new to ubuntu. I am using it for the first time. And I really need  your help. I have a laptop having configuration : intel pentium  processor p6100., 500GB HDD, 14 inch screen, 2GB ddr3 ram. 

The problem I am facing is ; I have chosen all of my disk space when I  was installing Ubuntu. I followed everything I could : like having the  dsl connection on thus the installation would include all updates and  plugins. The installtion completed successfully.  But when I restarted  my Laptop then it started in full screen terminal promt with the user I  created.  I tried several times to get to the GUI screen by  command  "startx", but the screen goes black / blank .  And after waiting 10/15  min I had to restart by pressing the power button.

Please help me to get to the GUI screen/mode.  Waiting for your valuable help. Thanks.

---

### Post by Daniel0108 on 2010-11-13
Hi!
Have you installed Ubuntu with GNOME?
or Kubuntu with KDE?
or another one?
You could reinstall it, if something went wrong with the installation. I think there is just no GUI installed :P
Yours,
Daniel

---

### Post by matt_symes on 2010-11-13
Hi

If you do have a desktop environment installed then you could try reconfiguring it (from a terminal)

sudo dpkg-reconfigure xserver-xorg

or restarting

sudo /etc/init.d/gdm start

Kind regards

---

### Post by arghyaghosh on 2010-11-13
Hi,
    As I said Daniel  , I am new to ubuntu...  I just downloaded the ubuntu dektop 10.10 iso image from the website and get it in a cd. I took it a complete disk using installation. As you said about the GNOME  , Honestly I don't have knowledge about it.  But what I did is choose complete installation and in that process I didn't get any option of choosing GNOME or such kind of option. I ran the whole installation process from the TRY(demo) mode of the CD. Is there I am missing some important steps?  ..... Thanks

IMPORTANT: Currently I dont have any other Operating system installed on the Laptop.

---

### Post by Daniel0108 on 2010-11-13
> **arghyaghosh said:**
> Hi,
    As I said Daniel  , I am new to ubuntu...  I just downloaded the ubuntu dektop 10.10 iso image from the website and get it in a cd. I took it a complete disk using installation. As you said about the GNOME  , Honestly I don't have knowledge about it.  But what I did is choose complete installation and in that process I didn't get any option of choosing GNOME or such kind of option. I ran the whole installation process from the TRY(demo) mode of the CD. Is there I am missing some important steps?  ..... Thanks

IMPORTANT: Currently I dont have any other Operating system installed on the Laptop.

Try entering:
```
sudo apt-get install gnome
```
into the console.

---

### Post by arghyaghosh on 2010-11-13
Thanks matt_symes[B], 

I am trying with that .. 

Thanks
[/B]

---

### Post by arghyaghosh on 2010-11-13
Hi All, 

Ok I am reinstalling it. If I face the same problem I will then follow yours help commands ..  

Thanks everyone.

---

### Post by Daniel0108 on 2010-11-13
> **arghyaghosh said:**
> Hi All, 

Ok I am reinstalling it. If I face the same problem I will then follow yours help commands ..  

Thanks everyone.
Okay, download the normal installer for UBUNTU :)
Not the alternative installer or Kubuntu ;)
Just Ubuntu :D
Yours,
Daniel

---

### Post by oldos2er on 2010-11-13
What video card?

---

### Post by arghyaghosh on 2010-11-13
Hi All,

        Yes I got the success at last. And I am very happy with it. I just love the Ubuntu.  Thing is; I did install the 10.10 version of it last time and for some unknown reason(unknown as I am new :) ) the GUI mode was not working for that. 

And now I just installed the 10.04 LTS and this one is superb. I want thank you all for your support and valuable help.

Cheers

---

### Post by Daniel0108 on 2010-11-14
> **arghyaghosh said:**
> Hi All,

        Yes I got the success at last. And I am very happy with it. I just love the Ubuntu.  Thing is; I did install the 10.10 version of it last time and for some unknown reason(unknown as I am new :) ) the GUI mode was not working for that. 

And now I just installed the 10.04 LTS and this one is superb. I want thank you all for your support and valuable help.

Cheers
Fine that you like Ubuntu :D
Now please mark this thread as solved :D
Yours,
Daniel

---

