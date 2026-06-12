---
title: "password reset??"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by vegetable92 on 2009-08-13
How can i reset the password on ubuntu 8.10.

---

### Post by vegetable92 on 2009-08-13
like is there something i can type in command to change the password or a way to make another admin account

---

### Post by aysiu on 2009-08-13
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by rsiddharth on 2009-08-13
> **vegetable92 said:**
> How can i reset the password on ubuntu 8.10.
Go to System--> Preferences --> About me . In the dialog box that appears , hit "change password ".

---

### Post by jrothwell97 on 2009-08-13
Welcome to the Ubuntu Forums!

To reset your password (assuming you've lost it and need to change it without knowing the old one), you need to know your username (the one you use to log in).

Restart the computer, and when the boot menu appears (you might need to press *escape* to make it appear) select one with *recovery mode* at the end. Once startup is finished, select *root* from the menu.

You will land on a full-screen terminal. Run

```
passwd *<username>*
```

replacing *<username>* with the name you use to log in. It'll ask for a new password.

Note that in a terminal, when you type a password in, the cursor doesn't move and no stars or dots appear. This is normal - your password is still going in.

Once you've finished, type

```
reboot
```

to restart the computer. All being well, you should be able to log in again.

Good luck!

---

### Post by vegetable92 on 2009-08-13
i can get into ununtu an it doesnt even ask for a password.but when i go to login window it asks for one.

---

### Post by colau on 2009-08-13
> **vegetable92 said:**
> How can i reset the password on ubuntu 8.10.
```

sudo passwd <username>
man passwd

```

---

### Post by go_beep_yourself on 2009-08-13
Ok, let me tell you how it's really done, on any machine, as long as the filesystem isn't LUKS encrypted.

Boot up a live CD

Mount the / (root) partition

Assuming your root partition is /dev/sda1

And replace root in the following command with your username you log in with.

[PHP]
sudo mount /dev/sda1 /mnt
sudo chroot /mnt
passwd <user name>
sudo reboot
[/PHP]

Remove the live cd.

You have just changed the password for of your Ubuntu installation.

If you need any more help, contact me via my blog in my signature.

:popcorn:

---

### Post by mcduck on 2009-08-13
> **go_beep_yourself said:**
> Ok, let me tell you how it's really done, on any machine, as long as the filesystem isn't LUKS encrypted.

Boot up a live CD

Mount the / (root) partition

Assuming your root partition is /dev/sda1

And replace root in the following command with your username you log in with.

[PHP]
sudo mount /dev/sda1 /mnt
sudo chroot /mnt
passwd <user name>
sudo reboot
[/PHP]

Remove the live cd.

You have just changed the password for of your Ubuntu installation.

If you need any more help, contact me via my blog in my signature.

:popcorn:

Why make the task that hard? All you really have to do is select the recovery option from boot menu, and once the system is running run a single command (passwd *username*).

---

### Post by go_beep_yourself on 2009-08-13
> **mcduck said:**
> Why make the task that hard? All you really have to do is select the recovery option from boot menu, and once the system is running run a single command (passwd *username*).

Because with Ubuntu, to boot into single usermode, you must know the password to get a root shell, but with the instructions I provided, you don't need to know any passwords to reset the password. Infact, I could easily provide information to get his original password in a matter of seconds using a md5hash exploit in the /etc/shadow.

:popcorn:

---

### Post by mcduck on 2009-08-13
> **go_beep_yourself said:**
> Because with Ubuntu, to boot into single usermode, you must know the password to get a root shell, but with the instructions I provided, you don't need to know any passwords to reset the password. Infact, I could easily provide information to get his original password in a matter of seconds using a md5hash exploit in the /etc/shadow.

:popcorn:

No, you don't need a password to boot into single user root shell. Try it if you don't believe. :)

(well, if you have set a root password you might need it, I'm not sure about that as I've never tried, but on normal Ubuntu setup you definitely don't need a password)

---

### Post by cariboo on 2009-08-13
If you have enabled the root account, you do need to enter a password when you drop to a root prompt.

Because of Ubuntu's security model, there really is no need to enable the root account.

---

### Post by rhcm123 on 2009-08-13
> **go_beep_yourself said:**
>  Infact, I could easily provide information to get his original password in a matter of seconds using a md5hash exploit in the /etc/shadow.

Can't you be banned for this?

---

### Post by go_beep_yourself on 2009-08-16
> **rhcm123 said:**
> Can't you be banned for this?

No, because whatever you do to your own computer is perfectly legal. Guns do not kill people. Men do. In other words, what you do with the information determines whether or not you get yourself into trouble.

---

### Post by go_beep_yourself on 2009-08-16
> **cariboo907 said:**
> If you have enabled the root account, you do need to enter a password when you drop to a root prompt.

Because of Ubuntu's security model, there really is no need to enable the root account.

You are very right. I enabled the root account. Something kept privelege dropping which would cause errors, but I can at any time remove the root account and therefor brute force attempts would do no or little good without a known user.

---

### Post by oboedad55 on 2009-08-16
> **mcduck said:**
> No, you don't need a password to boot into single user root shell. Try it if you don't believe. :)

(well, if you have set a root password you might need it, I'm not sure about that as I've never tried, but on normal Ubuntu setup you definitely don't need a password)

What's your grub line look for recovery mode? I use grub from another installation and edit menu.lst by hand.

Thanks!

---

### Post by mcduck on 2009-08-16
> **oboedad55 said:**
> What's your grub line look for recovery mode? I use grub from another installation and edit menu.lst by hand.

Thanks!

Same as normal boot, just add "single" to boot options. (and remove "quiet" and "splash").

---

### Post by oboedad55 on 2009-08-16
> **mcduck said:**
> Same as normal boot, just add "single" to boot options. (and remove "quiet" and "splash").

Okay, thanks for the help. So I can just add this at boot time by changing the parameters I already have set. In other words I would remove "quiet" and "splash" and replace them with the word "single". Correct?

Cheers,

---

### Post by mcduck on 2009-08-16
> **oboedad55 said:**
> Okay, thanks for the help. So I can just add this at boot time by changing the parameters I already have set. In other words I would remove "quiet" and "splash" and replace them with the word "single". Correct?

Cheers,

Yes, setting the parameters directly from Grub works just fine if you don't want to have the recovery mode permanently in your Grub menu.

---

### Post by oboedad55 on 2009-08-16
> **mcduck said:**
> Yes, setting the parameters directly from Grub works just fine if you don't want to have the recovery mode permanently in your Grub menu.

Thank you kindly!

---

### Post by colau on 2009-08-16
Thread can be marked as SOLVED.

---

