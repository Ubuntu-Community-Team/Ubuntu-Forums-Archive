---
title: "Auto-login not mounting encrypted home in karmic, unusable system"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by humphreybc on 2009-11-01
[b] EDIT:

Aha!! I worked it out. The GDM settings are stored in /etc/gdm/custom.conf so all I had to do was go into a virtual terminal and edit this file to change AutoLogin to false. Problem solved!

But, the question is... shouldn't an encrypted /home be mounted on auto login if specified? Actually, yeah, I know, what's the point of encrypting your home directory when you give the person access straight away... duh!

Maybe a warning is applicable in the "Login Manager" window, ie, when you check "enable auto login" it should prompt a warning saying "Do not enable auto login if you have encrypted your home directory" or something...

-------

[/b]

Hi guys,

I just installed Karmic final 64 bit onto my Mums new computer, an Asus PRO59le. Everything seemed to be running fine and I've been configuring it and updating/installing software for the past couple of hours.

I've done a few successful reboots with no problem.

Now, I have a problem. I turned on "auto login" to make it easier for her to boot up, but now I am getting errors when I bootup and it aint working. I'm pretty sure it's because the encrypted home directory is not getting mounted on login, because I turned on auto login. 

Ubuntu will boot and show the first splash screen, then the second splash screen and then it will load X. It'll then display this message in a box with a close button:

```

Could not update ICEauthority file /home/sandy/.ICEauthority

```

then immediately following:

```

There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)

```

Then this error:

```

Nautilus could not create the following required folders: /home/sandy/Desktop, /home/sandy/.nautilus

```

And then the wallpaper will load, but there will be no panels or icons or anything.

So basically, how do I turn OFF auto login in a virtual terminal/recovery console?

---

### Post by mulima on 2009-11-01
hi
same troubles here


you can do
```
sudo chmod a+w /home/user 
```

for the .ICEauthority issue, this should solve your problems

auto login + encrypted home does not mount it automaticly.. this a a karmic bug i think ..

---

### Post by humphreybc on 2009-11-01
Yeah but as I said in the edit, if you are worried enough to encrypt your home folder to prevent access, then you probably shouldn't be enabling auto login!

To turn auto login off you can go into recovery console or a virtual terminal and type:

```

sudo nano /etc/gdm/custom.conf

```

And change the AutoLogin entry to "false" then reboot

---

### Post by b0b138 on 2009-11-01
I came across this same problem. While I never found a solution, I could ctrl-alt-f1 a virtual terminal, login, and restart gdm (sudo /etc/init.d/gdm restart) and it would be fine. Its almost like with autologin its trying to access /home before it got decrypted.

---

### Post by thunderbear on 2009-11-03
Hi

i have exactly the same problem as detailed above with the same error messages, but unable to recover have tried all the answers detailed, just get to the orange screen, no doubt because my home directory remains encrypted

any other ideas as to how to recover, else this is this a bug???

---

### Post by Jonathan Gossage on 2009-11-05
You can recover quite easily with the following procedure.

1. When you get the blank screen instead of a usable desktop, type Ctrl-Alt-F1 to bring up a TTY console and login.

2. Enter the following command:
   sudo shutdown -r now

3. When the GDM login screen is presented, click on the link that allows you to login with another user id.

4. Enter your user name and hit enter to bring up the password prompt.

5. Enter your password at the password prompt.

6. When the desktop comes up goto System->Administration->Login Screen and disable automatic login.

Auto login is incompatible with the encrypted home directory since the password is required at login time to decrypt the home directory and auto login does not allow you to enter a password.

---

### Post by elect on 2009-11-15
Over disabling the auto login, is there maeby a way to keep away the encryption? ^^

---

### Post by The End of The World on 2009-11-25
OMG THANKYOU!

you saved me hours of coursework :) thankyou - i thought i had lost it all!

*praises*
*insert more praises*

---

### Post by scorp123 on 2009-11-25
> **b0b138 said:**
> Its almost like with autologin its trying to access /home before it got decrypted. The password serves as passphrase too. With "autologin" you don't enter a password == home directory CAN NOT be decrypted unless you login and supply your password.

I think the installer mentions this even.

And OP is right ... what's the point of encrypting your /home directory if you want any thief to have instant access to your data anyway? What's the point?

The point of encrypting your /home is precisely this that without knowledge of your password the data CAN NOT be accessed, even if your computer were to be confiscated and what not.

Without disk encryption anyone having physical access to your computer CAN and WILL get access to your data, no matter if they know your username or password or not.

So the purpose of encrypting your /home folder is to close this attack vector. But if you set your computer to "autologin" (e.g. because it's a desktop PC at home and you're never ever travelling with it anyway) ... why then the encryption?

If disk encryption worked the way you guys thought it would work then it would be totally pointless.

And sorry if I sounded rude, harsh and what not. I didn't mean to. It's just that I find the thought of having disk encryption AND "autologin" working together downright horrible from a security POV. So please nobody feel attacked or something ...

---

### Post by crowdedelevator on 2010-01-07
i still get the configuration server code, but never had the nautilus code.
although im a noob

---

### Post by Darce on 2010-01-09
Thanks to the OP

Same problem here, although I don't remember turning on Autologin !?!

Solution was the same and worked perfectly.

Love these Forums.

Thanks guys :)

---

### Post by Redsandro on 2010-01-11
I've had [exactly the same problem]("http://ubuntuforums.org/showthread.php?t=1373476"), but at first I didn't understand why and missed this topic.

Ofcourse it's all fixed now that I don't use autologin, but I was wondering.. is there some way I can use autologin WITH an encrypted homedir?

---

### Post by r1ch on 2010-01-11
Brilliant! Thankyou for the solution, it worked perfectly!

---

### Post by Redsandro on 2010-01-11
I understand auto-login cannot work with home encryption. Well Ubuntu could have at least made a nice message box saying: "Sorry this is not available because of this and this." 'Cause now it had to scare the crap out of me.

> **scorp123 said:**
> The password serves as passphrase too. With "autologin" you don't enter a password == home directory CAN NOT be decrypted unless you login and supply your password.
So out of curiousity, how does auto-login work without a password? There's a "flag" saying login and it just doesn't need a password? I can boot from usb in my collegue's computer, write one bit from false to true, and login without his password?

> what's the point of encrypting your /home directory if you want any thief to have instant access to your data anyway? What's the point?

The point of encrypting your /home is precisely this that without knowledge of your password the data CAN NOT be accessed, even if your computer were to be confiscated and what not.

The world is not black and white with friends or criminals. I know a lot of script kiddies who find it easier to boot portable windows, mount my home dir and mess with my files than just to work with linux. It's an extra layer of trouble one has to go through to get to my files. It's not like I want to hide my suspective browser history from the FBI or something. No if they really want my home dir they can have it.

---

### Post by ben2talk on 2010-05-16
Great work guys - I actually found the solution booting from my spare USB (installed Karmic there, to save booting from slow CD...) and disabled the auto-login.

This brings an issue - something I discovered with the failed encryption setup (when I first installed).

So I now use dropbox to sync all of my important /home/ben contents, and I have another hard disk - which I use for all my pictures and documents (so only stuff left at /home/ben is encrypted, but not documents or anything else...)

Ubuntu is safe from others, but often will take away our own files too!!!

---

### Post by Redsandro on 2010-05-17
BTW awesomeness, I deleted /usr etc when I wanted to install Lucid, but I forgot to decrypt my /home. FFFFUUUUU...!!!

Luckily, if you install over your homes and use the exact same password for users, it will be mounted just fine. Phew.

---

### Post by Joe Question on 2010-06-17
[QUOTE=Jonathan Gossage;8251685]You can recover quite easily with the following procedure.

1. When you get the blank screen instead of a usable desktop, type Ctrl-Alt-F1 to bring up a TTY console and login.

2. Enter the following command:
   sudo shutdown -r now

3. When the GDM login screen is presented, click on the link that allows you to login with another user id.

4. Enter your user name and hit enter to bring up the password prompt.


Hi! I am stuck with the same problem, tried to follow this procedure but when I get to point four and hit enter it does not bring up the psw prompt. 
It just goes back to the "blank" desktop.

I also tried every other procedure in this post like changing the gdm with nano but it didn't work out and I restored all the original values. 

I also created another user with administrator rights through the terminal, but it did not work (after requesting the password it would go to the blank desktop). 

Everything was working perfectly until I went into accounts and changed the settings so that no password would be requested at login. Beforehand I had already set autologin, to no effect as it keept asking for a psw in the login screen. 

Could anyone save me from a looooong re-install?
Cheers!

---

