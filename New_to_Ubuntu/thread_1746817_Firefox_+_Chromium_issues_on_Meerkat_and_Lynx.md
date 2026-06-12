---
title: "Firefox + Chromium issues on Meerkat and Lynx"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by Goliath99 on 2011-05-02
Hi there

I've been using Ubuntu since Hardy Heron, and apart from a few hardware issues back then, I haven't had any problems.

A few months ago I installed Lucid Lynx on my desktop. All was well until one day most of the images on my Facebook page disappeared.
Pretty annoying.
Then I went to check my email. Clicked on my hotmail bookmark, and was greeted by a "server not found" page, yay.

I installed Opera, and this let me see a few more images on FB, but still wouldn't let me visit hotmail.


Fortunately my netbook, running Karmic NBR was still 100% usable.
So I didn't bother trying to fix the desktop.

Then, I upgraded the netbook to Meerkat. Low and behold the exact same firefox issues appeared.
Not one single fix for this problem seems to work.
So, I installed Linux Mint 10. This was mainly because of the STUPID amount of space that the new sidebar takes up. I also hoped it might fix firefox - No luck.

I installed Chromium from the repos, and facebook started working again!! I could even check out my hotmail.
I thought this was amazing, and wondered if firefox might have fixed itself, so I checked FB and hotmail on there - still broken.
Immediately after doing that, Chromium gave the "Server not found" page for hotmail.

I hope that gives a clue as to what might be causing the problem.


Any help would be appreciated.

Thanks.

---

### Post by Goliath99 on 2011-05-06
Any ideas?

---

### Post by Goliath99 on 2011-05-20
Update:

I cant log onto youtube, google, and hotmail.
Facebook is also completely unusable.

---

### Post by josephmills on 2011-05-20
huh maybe firewall issue? set to high? look into that tell us if you get anywhere. is it your isp firewall?

---

### Post by Goliath99 on 2011-05-20
Cool.
How would I go about doing that? Sad to say that after all these years, I'm still more comfortable on windoze.

What bugs me the most, is how random this is. One day all will be fine. The next, some things work, and others don't.

The day I created this user profile, I couldn't log in to hotmail to retrieve the password for my original profile. So I created a gmail account. Now I cant even log into that?

---

### Post by josephmills on 2011-05-20
> **Goliath99 said:**
> Cool.
How would I go about doing that? Sad to say that after all these years, I'm still more comfortable on windoze.

What bugs me the most, is how random this is. One day all will be fine. The next, some things work, and others don't.

The day I created this user profile, I couldn't log in to hotmail to retrieve the password for my original profile. So I created a gmail account. Now I cant even log into that?


go up to the network manager icon and right click it. Now select connection information then open your browser any and type in your default route then a page will come up it will ask for a name and a password but before we can log into you router we all need to know what kind of router you have so we can put in the default password and username (it is usually admin or nothing for the user account and password or admin or passwrd for the password  ) but lets make sure what kind of router do you have?

---

### Post by Goliath99 on 2011-05-20
Its a TP-Link, and I've logged in.

Whats next:-)

---

### Post by josephmills on 2011-05-20
> **Goliath99 said:**
> Its a TP-Link, and I've logged in.

Whats next:-)

go to the security settings and see if the firewall is on high if so bring it down to med if you have troubles shoot us some screen shots BUT please dont show off personal info

---

### Post by Goliath99 on 2011-05-20
No luck.

The only reference to firewall on there was 'SPI Firewall', with only enable or disable options.
No effect with either.

What should I take a screenshot of?

---

### Post by josephmills on 2011-05-20
no that is ok try to disable it for a sec to see if that is it then enable it again and post back

---

### Post by Goliath99 on 2011-05-20
It didn't make a difference:-(

---

### Post by bdoe on 2011-05-20
I've had some pretty random and bizarre issues with Flash, particularly on my kids' laptops running Mint LXDE. I am starting to wonder if there's some sort of conflict between the flash plugin typically installed with Firefox, and Chrome/Chromium's own built-in flash plugin. What happens if you completely uninstall the Adobe flash plugin?
```
sudo apt-get remove --purge adobe-flashplugin
```
Once you remove it, sites that use flash won't work on Firefox, but if my theory is correct, everything should work fine on Chromium.

Edit: Forget what I said here. I just realized that one of the things that sets Chromium apart from Chrome is that Chrome has its own built in flash plugin whereas Chromium does not.

---

### Post by josephmills on 2011-05-20
arghh what os are you using right now? and the kernel too please and thanks

---

### Post by Goliath99 on 2011-05-20
I'm using Mint 10
Kernal 2.6.35-22

---

### Post by josephmills on 2011-05-20
this has got to be on your isp side install ubuntu 10.10 and then update it and upgrade it post back when done thanks

---

### Post by Goliath99 on 2011-05-20
This same thing happened on 10.10, thats why I'm trying Mint.
Its also happening right now on my 10.04 desktop.

---

### Post by josephmills on 2011-05-20
what happens when you use traceroute? ```
traceroute www.google.com 
``` please do NOT post the out come here you can send me a personal message of it if you like.

---

### Post by Goliath99 on 2011-05-20
I cant seem to download traceroute through terminal or synaptic.
Is tracepath the same thing?

This is what tracepath found: 
Too many hops: pmtu 1480
     Resume: pmtu 1480

---

### Post by josephmills on 2011-05-20
I really think that you isp has some thing to do with this lets ah please go to password and encryption keys and and removal all that are for your gmail facebook or whatever then unimstall chrouim then re-install it and see if that does any thing are you using wireless for this?

---

### Post by Goliath99 on 2011-05-20
I'll have to try this tomorrow, as I'm starting to fall asleep. 

Thanks for the help so far:-)

---

### Post by Goliath99 on 2011-05-21
Before I uninstall everything...
I just hooked my HTPC(Running XP) up to the wifi network. 
I've got firefox 4 on there and its running flawlessly. 
Everything works.

What was the fundamental change between Karmic and lynx/meerkat, that made everything go mental?

---

### Post by Goliath99 on 2011-05-22
Here are screenshots of facebook on firefox and chromium respectively:

[img]/home/emile/Desktop/Screenshot.png[img]

[img]/home/emile/Desktop/chromium fb.png[img]

If those screenshots don't appear, its because I tried to insert them without using the 'insert image' tab. It just refused to do anything.

---

