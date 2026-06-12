---
title: "change my password"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by jrev on 2010-02-14
Hi all,

I am on ubuntu 9.10. I have chosen to connect automatically the first user.
Then I forgot my password and cannot enter the recovery boot to change it.

My question : can I create a new password from a live CD ?

How do I do that ?

Thanks for your help

---

### Post by pavel989 on 2010-02-14
my only guess would be to chroot into your install and run passwd. however id assume that you need the password to do that. maybe not, id give it a try

---

### Post by hashimoto on 2010-02-14
> **jrev said:**
> Hi all,

I am on ubuntu 9.10. I have chosen to connect automatically the first user.
Then I forgot my password and cannot enter the recovery boot to change it.

My question : can I create a new password from a live CD ?

How do I do that ?

Thanks for your help

Push "ESC" during boot to get to Grub and select recovery from the list. You will then be booted to recovery mode as root. Change your password with: 

```
passwd [yourusername]
```

and enter the new password. 

Then reboot with:

```
shutdown -r now
```

---

### Post by jrev on 2010-02-14
According to [www.psychocats.net](www.psychocats.net) :

Note for Ubuntu 9.10 (Karmic)
Karmic no longer has the ability to show the boot menu by pressing Escape. To get the boot menu to show, you have to hold down **[COLOR="black"][COLOR="Blue"]the Shift key during bootup.[/COLOR][/COLOR]**


From the boot menu, select recovery mode, which is usually the second boot option.


After you select recovery mode and wait for all the boot-up processes to finish, you'll be presented with a few options. In this case, you want the Drop to root shell prompt option so press the Down arrow to get to that option, and then press Enter to select it.

The root account is the ultimate administrator and can do anything to the Ubuntu installation (including erase it), so please be careful with what commands you enter in the root terminal.

---

### Post by hashimoto on 2010-02-14
> **jrev said:**
> Note for Ubuntu 9.10 (Karmic)
Karmic no longer has the ability to show the boot menu by pressing Escape

Oops!

Can't even remember when I last needed to boot to root shell. Makes my feeble skills outdated and shows how good Ubuntu has become...

---

### Post by jrev on 2010-02-14
But is there a way to change a word in a file from the CD live ?

---

### Post by sisco311 on 2010-02-14
> **jrev said:**
> But is there a way to change a word in a file from the CD live ?

[noparse]The encrypted password is stored in the [mount/point]/etc/shadow file. Fields are separated by a colon (:). i.e:[/noparse]
```

**username**:[COLOR="Red"]$6$lyT.wMxN$snxnZNwm9OPexPaIHWJI1iOA17/24ZYoBqryOMMLddyBXHFA5pmY2uxj5r3q87t.Bglwh80hM9qWQC2FaEBao.[/COLOR]:14654:0:99999:7:::
```
[http://www.cyberciti.biz/faq/understanding-etcshadow-file/](http://www.cyberciti.biz/faq/understanding-etcshadow-file/)

The **first field** is the **username**, the [COLOR="Red"]second[/COLOR] one is the [COLOR="Red"]encrypted password[/COLOR].

To change your password to the word **password**, replace the value with:
```

$6$lyT.wMxN$snxnZNwm9OPexPaIHWJI1iOA17/24ZYoBqryOMMLddyBXHFA5pmY2uxj5r3q87t.Bglwh80hM9qWQC2FaEBao.

```

To generate an encrypted password, you can use the 
```
mkpasswd -m sha-512
```command.

[COLOR="Red"]BE CAREFUL[/COLOR], **backup the file before editing it!**

---

### Post by jrev on 2010-02-16
to change my password with the SystemRescueCD :
Boot on it and find out your / system identity by :> fdisk -l 

---

