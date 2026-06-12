---
title: "Chrome settings, making plymouth splash work, &quot;open as root&quot;, decimal sign in OO"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by flyver on 2010-05-21
Many questions.

I tried making the standard Ubuntu 10.04 splash work, and in the end (after having read many posts here) I tried uninstalling "plymouth" and all the dependencies (wanted to re-install all of that right afterwards)...seems I shouldn't have done that. Lost everything.

Anyway, I am now running Linux Mint Isadora from a flash drive and can access my files and folders.

[LIST=1][*]1 Is there any way I can save the settings of my Chrome? I had this "Speed dial" extension and spent some time setting it up, I was wondering whether I could find a file where it is saved and copy it to my freshly installed Ubuntu 10.04 (when I decide to re-install it).

[*]2 Is there any way to make Plymouth/splash work? My screen is black while the computer boots up.

[*]3 In Linux Mint, you can right-click a folder or file and select "open as root" (or in the newest release "open as administrator"). Is there any way to add this function to Ubuntu?

[*]4 I used to save this .xls file in Windows, with the decimal sign being comma. For some reason, when I changed to Ubuntu, OpenOffice (spreadsheet) changed all my commas to period signs. I don't want that and I wonder: is there any way to make it go back to commas, and make OpenOffice understand that 1,3 + 1,7 = 3? Now it doesn't understand that, even though I have changed the computer regional settings to Norwegian, and the OpenOffice settings to Norwegian as well.

[/LIST]

Thank you for any answer.

---

### Post by cariboo on 2010-05-21
> 1 Is there any way I can save the settings of my Chrome? I had this "Speed dial" extension and spent some time setting it up, I was wondering whether I could find a file where it is saved and copy it to my freshly installed Ubuntu 10.04 (when I decide to re-install it).

All of the chrome files you need to save are located in ~/.config/google-chrome

> 2 Is there any way to make Plymouth/splash work? My screen is black while the computer boots up.

It depends on what video drivers you are using, plymouth works better with the open sources drivers.

> 3 In Linux Mint, you can right-click a folder or file and select "open as root" (or in the newest release "open as administrator"). Is there any way to add this function to Ubuntu?

There is a package in the repositories called nautilus-gksu, that will add that function.

> 4 I used to save this .xls file in Windows, with the decimal sign being comma. For some reason, when I changed to Ubuntu, OpenOffice (spreadsheet) changed all my commas to period signs. I don't want that and I wonder: is there any way to make it go back to commas, and make OpenOffice understand that 1,3 + 1,7 = 3? Now it doesn't understand that, even though I have changed the computer regional settings to Norwegian, and the OpenOffice settings to Norwegian as well. 

I'm not sure about this problem, but it may be a locales problem.

---

### Post by flyver on 2010-05-22
Thanks for your reply, this should be very helpful!

And while I'm at it, I've read lots of posts about wireless connection problems, and also found some people who had the very same symptoms as I (but no fix). What happens is that after a suspend (or hibernate) session, the wireless applet ... or whatever it is called, doesn't want to turn on, it just says no networks are there. ("Enable networking" + "enable wireless" is ON, and my wireless connection is made to "connec automatically".)

I will get back to this post as soon as I have figured whether your recommendations work.

Thank you.

---

### Post by flyver on 2010-05-23
1: Regarding question number 1, Chrome wasn't able to "find all my settings" (actually, it doesn't seem to have worked at all), but it isn't that big a deal.

2: Regarding Plymouth, the information I could find regarding my graphics is this: *Intel GM965/GL960 integrated graphics controller.* You mention "video driver" and I guess that is something else. I have no idea how to find this.

3: About "open as root", this works perfectly, thank you!

And 4: After the re-installation of Ubuntu, I managed to change things so that OO understands that 1,1 + 1,2 = 2,3.

When I find out how to make Ubuntu connect to my wireless after a "suspend session", I will truly love this operating system.

Thanks!

---

### Post by pborman on 2010-05-29
To get wireless working after a suspend/hibernate I have to go to network manager applet, disable wireless, then enable wireless again and it all works. Hope this helps for you too.

---

### Post by flyver on 2010-05-30
That doesn't help in my case =/

---

### Post by flyver on 2010-06-05
Regarding problem number 2, I have found a way to make the splash screen (Plymouth) work!

```
sudo update-alternatives --config default.plymouth
```
Then I chose the splash theme whose description differed the most compared to mine (mine was *0, I chose 2)

Then:
```
sudo update-initramfs -u
```

Then I did a reboot, then I did the same thing over again, only this time I selected the original splash theme.

And that's it!

Reference: [http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html)

---

