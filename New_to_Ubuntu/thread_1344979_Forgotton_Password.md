---
title: "Forgotton Password"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by Bellboy42 on 2009-12-03
Hello i have a Asus Eee Pc 701SD.....The problem is that my daughter as forgoten her SIGN IN...PASSWORD. Iv tried loading recovery disc though external cd/dvd reader via usb lead, but nothing happens.
 
How can i remove the password as i want to load vista onto the machine.
 
Is there a factory default password that i could use.
 
Looking forward to some help.
 
Thanks In Advance
 
Tony

---

### Post by DasEi on 2009-12-03
SO need recovery for win or ubuntu ? which distro ?

---

### Post by coffeecat on 2009-12-03
> **Bellboy42 said:**
> Hello i have a Asus Eee Pc 701SD.....
 
<snip>

  i want to load vista onto the machine.

Vista? On an EeePC 701? :shock: Are you sure? :-s

---

### Post by lisati on 2009-12-03
> **Bellboy42 said:**
> Hello i have a Asus Eee Pc 701SD.....The problem is that my daughter as forgoten her SIGN IN...PASSWORD. Iv tried loading recovery disc though external cd/dvd reader via usb lead, but nothing happens.
 
How can i remove the password as i want to load vista onto the machine.
 
Is there a factory default password that i could use.
 
Looking forward to some help.
 
Thanks In Advance
 
Tony
You shouldn't need your sign-in password to install another OS.......

---

### Post by Bellboy42 on 2009-12-03
system is Linux

---

### Post by adaucourt on 2009-12-03
> **Bellboy42 said:**
> Hello i have a Asus Eee Pc 701SD.....The problem is that my daughter as forgoten her SIGN IN...PASSWORD. Iv tried loading recovery disc though external cd/dvd reader via usb lead, but nothing happens.
 
How can i remove the password as i want to load vista onto the machine.
 
Is there a factory default password that i could use.
 
Looking forward to some help.
 
Thanks In Advance
 
Tony

If you are installing a new OS just format current install with the bootable installation disc, no password required.

---

### Post by HunterThomson on 2009-12-03
I think the default setting in Ubuntu is to encrypt the passwords with MD5 in the /etc/shadow file. You can go in there and then copy out the MD5 password hash then crack it with jhon the ripper.

If you only need to boot you can use Konboot
[http://www.piotrbania.com/all/kon-boot/](http://www.piotrbania.com/all/kon-boot/)

---

### Post by coffeecat on 2009-12-03
> **Bellboy42 said:**
> system is Linux

Hang on. Let's start again.

The Asus EeePC comes with Xandros. Is that what you've got installed, or did you install some variant of Ubuntu? Because it makes a difference. Restoring the Administrator password in Ubuntu is quite easy, but there won't be many people who'll be familiar with the version of Xandros that comes on the Eee. It's very different.

Second, as lisati said, if you want to install another OS, you won't need the password. Simply use the OS installer to reformat the SD/HD and install away.

BUT - Vista? I've got an EeePC 701. There's not a snowflake in hell's chance of installing Vista to a 701. It's far too underpowered. Too little RAM. SD too small. CPU too slow.

---

### Post by estamand on 2009-12-03
To reset password:

[LIST]
[*]Shutdown
[*]Power on and hit ESC at the grub prompt
[*]Finder your kernel and press 'e'
[*]Goto the line that starts with 'kernel' and press 'e'
[*]At the end add 'single' without the quotes
[*]Press Enter
[*]Press b to boot
[*]Once you see the menu choose "Drop to root shell"
[*]Change your password using "passwd newpassword"
[/LIST]

---

### Post by HunterThomson on 2009-12-03
> **estamand said:**
> To reset password:

[LIST]
[*]Shutdown
[*]Power on and hit ESC at the grub prompt
[*]Finder your kernel and press 'e'
[*]Goto the line that starts with 'kernel' and press 'e'
[*]At the end add 'single' without the quotes
[*]Press Enter
[*]Press b to boot
[*]Once you see the menu choose "Drop to root shell"
[*]Change your password using "passwd newpassword"
[/LIST]

Nice that is a way better way.

---

### Post by bsharp on 2009-12-03
> **coffeecat said:**
> Hang on. Let's start again.

The Asus EeePC comes with Xandros. Is that what you've got installed, or did you install some variant of Ubuntu? Because it makes a difference. Restoring the Administrator password in Ubuntu is quite easy, but there won't be many people who'll be familiar with the version of Xandros that comes on the Eee. It's very different.

Second, as lisati said, if you want to install another OS, you won't need the password. Simply use the OS installer to reformat the SD/HD and install away.

BUT - Vista? I've got an EeePC 701. There's not a snowflake in hell's chance of installing Vista to a 701. It's far too underpowered. Too little RAM. SD too small. CPU too slow.

This. 

You would have a hard time getting XP to run on a EeePC 701, much less Vista.

---

