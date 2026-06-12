---
title: "help! My Ubuntu is messed up!"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by kramer65 on 2010-05-08
Hello,

Yesterday I watching some youtube vids and had Openoffice running as Ubuntu suddenly froze. I had to do a hard-reset, after whcih Ubuntu seemed to start up fine. However, when I now click "Applications" the menu doesn't show. It just shows a tine little white box of maybe 5mm, but nothing else. When I click "system"  it shows the drop down, but without the preferences or administration options.

 This has made Ubuntu almost useless! Does anybody have any idea what I could do? Isn't there a way to do some kind of system restore or something?

All help is welcome!

---

### Post by Bob Bertrands on 2010-05-08
You can try reinstalling the "desktop"layer of ubuntu if your problem is located there

---

### Post by unmole on 2010-05-08
Hit Alt+F2 and type ```
gnome-terminal
```
Then type in ```
sudo debconf gnome-panel
```
Enter your password. this will reset the gnome panel to default settings and hopefully fix your problem.

---

### Post by spiky001 on 2010-05-08
re the resy of the applets there

---

### Post by kramer65 on 2010-05-08
Thanks for all the quick answers!
Unmole, I tried your tip, but I get two error messages:

```
** Message: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name

** (gnome-panel:2423): WARNING **: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name
```

It works for as long as you stay logged in. But when I then restart, the problem is back again. Is there a way to permanently do that thing (the "debconf gnome-panel" thing)?

---

### Post by kramer65 on 2010-05-08
If there is no way of keeping this permanent, is there then a way to reinstall that part so that it is clean again?

---

### Post by kramer65 on 2010-05-08
Does the fact that nobody responds mean that there is no other way than reinstalling Ubuntu? 

I've got my /home folder on a separate partition. I presume this means I keep all my settings. Does it also mean that I keep all my installed programs, or do I need to reinstall them after a fresh ubuntu installation?


I just remember that Bob Bertrands suggested reinstalling the desktop part of Ubuntu. In another thread I saw this:
```
sudo aptitude reinstall ubuntu-desktop
```
The thread in which I read this was from 2006, so I am not really sure whether that would still apply. Would this be the action to reinstall the desktop part what was meant before?

---

### Post by wilee-nilee on 2010-05-08
I think you have had little response, due to the cause and effect makes no sense. I would do a memory check at boot and let it run for awhile. Check to see how the computer runs on a thumb if you can boot from one, a ssd will give you a faster running OS in general then a Live CD. Here is a link to do soft shut downs.
[http://en.wikipedia.org/wiki/Reisub](http://en.wikipedia.org/wiki/Reisub)

---

### Post by kramer65 on 2010-05-08
Hi Wilee-nilee. I restarted many times now, and the last time it started a disk check. Is that wjat you mean by a memory check? If not how would I do that?

Also, what does "running on a thumb" mean?

Do you possibly know a way to make that command "sudo debconf gnome-panel" be permanent? And do you know if "sudo aptitude reinstall ubuntu-desktop" would be a good idea?

Sorry, lost of questions, but I'm kinda lost here..

---

### Post by spiky001 on 2010-05-08
hi If you click say on the bottom panel can you add menu bar? that is applications /places/system. the reason i said ad to bottom bar is to see if all works there 1st then maybe remove the top 1 if works and add that to top after if it works

---

### Post by kramer65 on 2010-05-08
On both the bottom and the top panel I can add the menu items, but those then have the same trouble as the original menu items; not showing the applications or the system items..

Would you have any other idea?:-(

---

### Post by spiky001 on 2010-05-08
sorry it was just a suggestion, would it be to much grief to reinstall is only a thought tho

---

### Post by Dougie187 on 2010-05-08
What happens if you right click on the some empty space on a panel and go to the option "Add to panel". Then scroll down to find "Main Menu" and add that.

If you click on the new menu (should be a smaller ubuntu logo) does the same thing happen?

---

### Post by sadaruwan12 on 2010-05-08
My advice to bro is to stop suffering and reinstall the system if you have you /home folder on a separate partition.

---

### Post by kramer65 on 2010-05-08
I indeed have my /home folder on a separate partition. But if I reinstall, do I need to reinstall all my programs as well? What exactly is saved in the home partition? 

Do I for example need to reinstall the theme I have (took me about an hour thelast time). And do I need to reinstall all my programs..?


The thing is that I rather keep this installation. With the help of the command "sudo debconf gnome-panel" things are oke. I just need to keep it that way so that it doesn't revert to the same problem when I restart..

---

### Post by lemming465 on 2010-05-10
> if I reinstall, do I need to reinstall all my programs as well?
Yes.

> What exactly is saved in the home partition? 
Whatever you put there.  This typically includes per-user application configuration files such as desktop theme choices, downloaded e-mail, web browser bookmarks, ripped CD tracks, etc.

If the *sudo debconf gnome-pane* gets you temporarily functional, open up a terminal window and try some stuff:```

sudo apt-get update
duso apt-get upgrade -f
sudo dpkg-reconfigure gnome-panel
sudo chown -R $USER.$USER $HOME
```
No guarantees, but these shouldn't make things any worse, and might make them better.

---

