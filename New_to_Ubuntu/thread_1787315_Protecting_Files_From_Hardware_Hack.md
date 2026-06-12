---
title: "Protecting Files From Hardware Hack"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by jkurtisr32 on 2011-06-21
Is it possible to protect your files (or just specific files) from someone using a bootable image? On my own system I am able to gain access to my root directory by booting to an Ubuntu bootable flash drive. I understand that someone would have to be physically at my computer to gain access to anything, but is it possible to protect my filesystem without having to password the 'boot to USB' feature on my motherboard?

Just wondering.

-Kurt

---

### Post by amjjawad on 2011-06-21
> **jkurtisr32 said:**
> Is it possible to protect your files (or just specific files) from someone using a bootable image? On my own system I am able to gain access to my root directory by booting to an Ubuntu bootable flash drive. I understand that someone would have to be physically at my computer to gain access to anything, but is it possible to protect my filesystem without having to password the 'boot to USB' feature on my motherboard?

Just wondering.

-Kurt

Some might be able to access your files remotely and don't have to be physically on your machine.

This might be not a real solution but if I were you, I would save my critical/personal files on an External Drive. 

I think (not sure) if you Encrypt your /home partition (which is an option you can do in the 6th or 7th step during installation) will give you some kind of protection but not sure if someone will boot from a LiveCD or USB will still be able to access your files or not? I've never tired the encryption option so better to wait for someone who has tried it :)

Hope that will help you a bit :)

---

### Post by Vaphell on 2011-06-21
one word - encryption
in fact ubuntu offers an option to encrypt home dir during installation
[http://www.ubuntugeek.com/encrypted-home-now-offerred-at-installation.html](http://www.ubuntugeek.com/encrypted-home-now-offerred-at-installation.html)

---

### Post by nzjethro on 2011-06-21
Yup, I'd vote to encrypt your home drive (or at least the folder containing your sensitive files). Otherwise, you could change the ownership of the files to you, requiring a password to access them, as they show you how to do in this thread. [http://ubuntuforums.org/showthread.php?t=1553670](http://ubuntuforums.org/showthread.php?t=1553670)

---

### Post by dFlyer on 2011-06-21
Yap just encrypt your home directory.

---

### Post by jkurtisr32 on 2011-06-21
Hey everyone,

Thanks for all the replies. Lots of good input.

Yeah, not really a pressing issue for me; I was more just curious. I'm rocking a setup where I have a more powerful machine running my applications and booting the os, and all of my data (desktop, downloads, files) is kept on a server where the filesystem is mounted at boot. Today I modified my fstab to use a "credentials" file, and it was awkward because it was the first time that I've seen my password spelled out in a file to see. The credential file is located in the /root dir, so its safe, but I was just thinking how I would get at it if I was up to no good. Just got me thinking.

Thanks, everyone.

-Kurt

---

### Post by mastablasta on 2011-06-21
the reason why we often see asterisks (or nothing) when typing a password is in case someone is standing behind us reading it (or if there is a camera). if all they can see is ****** it's hard for them to know what we typed in. otherwise if you are alone at home it makes no difference if this password is disclosed or not. if you look at some encryption software (for example keepass - handy software keeps passwords to various sites encrpyted by one big password) you will see that often you can choose to disclose the *****
 
also i dont' know if you noticed but often you can copy the ****** into the other field. if oyu can copy text then you can paste it somewhere else too ;-)

---

### Post by Rolly banez on 2011-06-21
you might wanna look for Frankenstein software. its hacker proof.

---

