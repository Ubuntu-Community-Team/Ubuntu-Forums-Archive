---
title: "Ubuntu 10.04 Freezes on Ligin"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by JonathanDS on 2010-08-14
My friend recently installed Ubuntu 10.04 on his HP laptop. It worked fine, until he let it suspend. When he woke it up, it froze. No keys worked. He hard booted his pc, and, when it loaded up to the login screen, it froze again. We tried to get past his login multiple times, but never managed it. Afterwards, we decided to try KDE. We installed Kubuntu 9.10, and set it to auto login. This worked, but any time he let it suspend, it froze. He's in college, right now, so this type of instability couldn't be tolerated. He is currently switched back to W7 Ult.

Anyone wanna try to shed some light on this occurrence?

---

### Post by blazemore on 2010-08-14
Hi there.
It would help us help you if you could provide us with the exact model of the laptop, if you know it.

Regardless of the laptop model, I'd like to know "how frozen" it is.
When you press keys like NumLock and CapsLock, do the lights change?
When you press "Ctrl + Alt + F1" does anything happen?

---

### Post by ikhwa on 2010-08-14
> **blazemore said:**
> Hi there.
It would help us help you if you could provide us with the exact model of the laptop, if you know it.

Regardless of the laptop model, I'd like to know "how frozen" it is.
When you press keys like NumLock and CapsLock, do the lights change?
When you press "Ctrl + Alt + F1" does anything happen?

I press "Ctrl + Alt + F1",[COLOR=#000000]and my computer screen turn into a terminal:confused:, how to restore it come back again, without restarting?  :confused:[/COLOR]

---

### Post by blazemore on 2010-08-14
> **ikhwa said:**
> I press "Ctrl + Alt + F1",[COLOR=#000000]and my computer screen turn into a terminal:confused:, how to restore it come back again, without restarting?  :confused:[/COLOR]

Although you may not realise it, that's good news! (To go back, use the key combination Ctrl + Alt + F7). It means your friend's laptop hasn't completely frozen up.

What has happened is that something called the "X Server" hasn't come back from sleeping properly. The X Server is the part of Ubuntu that deals with drawing everything graphical on the screen.
This explains why you can get a basic terminal but no fancy user interface.

Unfortunately my knowledge of X isn't that great, but I do have one suggestion:
Hit Ctrl + Alt + F1 one more time, then log in to the terminal that appears.

Enter the following command carefully, then hit Enter:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

After you hit Enter, it will ask for the password again, just type it in and press Enter.

Reboot (the command is "sudo reboot now") and see if it works after that.

---

### Post by JonathanDS on 2010-08-14
> **blazemore said:**
> Hi there.
It would help us help you if you could provide us with the exact model of the laptop, if you know it.

Regardless of the laptop model, I'd like to know "how frozen" it is.
When you press keys like NumLock and CapsLock, do the lights change?
When you press "Ctrl + Alt + F1" does anything happen?

I'm not sure about the exact model. I know it's an x86, with a dual core.  As for the keys, none of them worked(CAPS Lock, NUM Lock, Touch Pad Toggle Button, CTRL, ALT, WIFI Toggle, etc), except the Power button(when held down to trigger a hard boot). CTRL + ALT+ F1 had no effect.

---

### Post by JonathanDS on 2010-08-14
> **blazemore said:**
> Although you may not realise it, that's good news! (To go back, use the key combination Ctrl + Alt + F7). It means your friend's laptop hasn't completely frozen up.

What has happened is that something called the "X Server" hasn't come back from sleeping properly. The X Server is the part of Ubuntu that deals with drawing everything graphical on the screen.
This explains why you can get a basic terminal but no fancy user interface.

Unfortunately my knowledge of X isn't that great, but I do have one suggestion:
Hit Ctrl + Alt + F1 one more time, then log in to the terminal that appears.

Enter the following command carefully, then hit Enter:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```After you hit Enter, it will ask for the password again, just type it in and press Enter.

Reboot (the command is "sudo reboot now") and see if it works after that.

THAT WAS NOT ME. IDK who that is, but he is not affiliated with me, or my friend. Unfortunately CTRL + ALT + F1 had NO EFFECT.

---

### Post by blazemore on 2010-08-14
> **JonathanDS said:**
> THAT WAS NOT ME. IDK who that is, but he is not affiliated with me, or my friend. Unfortunately CTRL + ALT + F1 had NO EFFECT.

Sorry I wasn't paying attention and didn't see the name. I assumed it was you, but I guess I'm just tired.
I'm looking into it for you, but it would be really helpful if you could give me the model of the laptop. Thanks.

[SIZE="1"]PS. There's no need to get angry; I'm the one who's trying to help you at ten to midnight so best not to tick me off too much.[/SIZE]

---

### Post by JonathanDS on 2010-08-14
> **blazemore said:**
> Sorry I wasn't paying attention and didn't see the name. I assumed it was you, but I guess I'm just tired.
I'm looking into it for you, but it would be really helpful if you could give me the model of the laptop. Thanks.

[SIZE=1]PS. There's no need to get angry; I'm the one who's trying to help you at ten to midnight so best not to tick me off too much.[/SIZE]
I was not angry, I just wanted to insure clarity, and avoid any confusion. I very much appreciate you taking the time to help me.

---

### Post by blazemore on 2010-08-14
OK no problem, you're welcome :-)

Try this:
Open a terminal and type in:
```
sudo gedit /etc/default/acpi-support
```

After you enter your password and press Enter, a text editor will come up. 

Somewhere there, if it isn't blank, will be the line
> POST_VIDEO=true

change this to say
> POST_VIDEO=false

If the line isn't there, or there's nothing there at all, just add the line at the end.

Then Save, and Exit the text editor and the terminal.

---

### Post by JonathanDS on 2010-08-14
I'm afraid I cannot attempt any of this until I convince him to give Ubuntu another try. I'll try convincing him when he comes over, in a few hours. I'll test these out, and give you an update, then.

Thanks,
Jon

UPDATE: It will be atleast a week before I can test any of these. I'll update, then.

---

