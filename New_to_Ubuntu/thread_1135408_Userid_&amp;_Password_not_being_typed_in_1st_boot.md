---
title: "Userid &amp; Password not being typed in 1st boot"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by dr.anandravi on 2009-04-24
Hi! Friends,
I am using ubuntu 8.10 in GRUB with XP and my system boots in ubuntu in default and in first boot I am unable to type my userid and password ,thus each time I have to reboot the system,then all works fine.Suggest me what to do as it irritates me rebooting every-time.

---

### Post by Didius Falco on 2009-04-24
What kind of system are you using? Has it been doing this from when you installed it, or have you added anything to it? I'n thinking specifically of video drivers and/or Compiz.

Give us some more details and there is a much better chance that someone will be able to help you.

As a temporary measure to keep the annoyance to a minimum, you can set up your pc to automatically log you in.  Right click on your Switch Users/Shutdown menu (It'll be at the top right if you haven't changed the panels around) and choose Setup Login Screen.

You'll have to enter your password to make any changes. Select the Security tab and click the little box at the top that says "Enable Automatic Login". That will allow you to use the drop-down list just below it. Select your user name there and you'll log on automatically from then on.

I'd still advise you to try and track down the problem, though. It could be symptomatic of something else.

---

### Post by dr.anandravi on 2009-04-26
Thanks for your kind advise,I will switch to automatic way.I am using Lenovo 3000Y500,and soon after installation in upto 1 or 2 boot it was ok and this was the same in two installations as I installed ubuntu twice.I will be wating for your suggestions.

---

### Post by cariboo on 2009-04-26
HAve you tried creating a new password for your user? If not start in recovery mode, at the menu select drop to root prompt and type:

```
passwd <username>
```

where <username> is your username without the brackets.

---

### Post by dr.anandravi on 2009-04-27
I tried as per your instruction but in recovery mode that root shell promt was not being selected so again I rebooted in recovery mode then only I changed the password.So problem exists.What to do next?

---

### Post by Didius Falco on 2009-04-28
I found this while doing a search, so I have no clue if it will work for you or not. It did work for several other, and they are all using Lenovo 3000 Y500 laptops, though.

Please post back the results, so I'll know if it works, in case the question comes up again.

You need to edit your menu.lst file. You can do this from within Ubuntu using a Terminal shell. The first thing to do is backup the menu.lst file, so you have a copy to restore if needed. In the Terminal window, type ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_bak
```Then type ```
gksudo gedit  /boot/grub/menu.lst 
```In the menu.lst file, you'll see a list of kernels, something like this:

```
title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid           e02ddaef-9065-4851-a66f-b417af080bc6
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e02ddaef-9065-4851-a66f-b417af080bc6 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet
```You want to add "i8042.reset" to the end of the kernel line, so the above would like like this:

```
title            Ubuntu 9.04, kernel 2.6.28-11-generic
uuid           e02ddaef-9065-4851-a66f-b417af080bc6
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e02ddaef-9065-4851-a66f-b417af080bc6 ro quiet splash i8042.reset
initrd        /boot/initrd.img-2.6.28-11-generic
quiet
```Try with just the top entry, the one you normally boot into. Save the file and reboot. Try it out for a while, reboot a few times and see if it makes a difference.

If it fixes it, remember to go back into the menu.lst file and add it to the end of all the other "kernel" lines.

Also, remember to edit your menu.lst every time you get a kernel update and add it to the new kernel lines.

I hope this fixes the problem - please post back and let us know.

---

### Post by dr.anandravi on 2009-04-29
Hi! I took a day time to post the reply bcz my problem only 50% solved.Now I am unable to tell whether it will accept the typing of Id, pwd. In yesterday's 6 boot 2 times it did not accept the typing.Today morning it did the same as at first boot it did not accept.
Please Suggest something more, as we are proceeding rt direction.
Thanks!

---

### Post by Didius Falco on 2009-04-30
I have one more thing to try. I found this by doing a search at the Lenovo forums:

Open a Terminal shell and type

```
locale | grep  LANG
```This will return the default language locale information. For example, even though I live in Australia, I use the US settings (I'm originally from the USA...), so what I get back is 

 > LANG=en_US.UTF-8Now you need to edit your menu.lst file again

```
gksudo gedit /boot/grub/menu.lst
```and add the locale info to it. For example:

 ```
title            Ubuntu 9.04, kernel 2.6.28-11-generic
uuid           e02ddaef-9065-4851-a66f-b417af080bc6
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e02ddaef-9065-4851-a66f-b417af080bc6 ro quiet splash i8042.reset
initrd        /boot/initrd.img-2.6.28-11-generic
quiet  
```would become

```
title            Ubuntu 9.04, kernel 2.6.28-11-generic
uuid           e02ddaef-9065-4851-a66f-b417af080bc6
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e02ddaef-9065-4851-a66f-b417af080bc6 ro quiet splash [COLOR=Red]locale=en_US[/COLOR] i8042.reset
initrd        /boot/initrd.img-2.6.28-11-generic
quiet  
```I made it red just to make it easier for you to spot - it'll be plain text in the menu.lst file.

Save, and test it out a few times and let us know if it cures the problem.

---

### Post by dr.anandravi on 2009-04-30
a lot thanks to you, I will let you know the development after observing it for a day.
Thanks!

---

### Post by dr.anandravi on 2009-05-03
Hi!
after two days problem reappeared what next to do?
Regards.

---

### Post by Didius Falco on 2009-05-03
That is great news!! Please mark this thread as solved by editing your first post and then clicking the **Go Advanced** button. From that screen, you can edit the title. Just click on the back end of it and start typing "solved" and it will offer offer suggestions to finish it. Save the post and you are done - that way others experiencing the same problem have a better chance of finding it, and hopefully, a solution.

Thank you for your kind words. I am glad I could be of help.

Regards

---

