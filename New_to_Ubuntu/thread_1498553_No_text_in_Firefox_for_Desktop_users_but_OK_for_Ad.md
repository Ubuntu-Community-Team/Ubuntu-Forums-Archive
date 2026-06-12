---
title: "No text in Firefox for Desktop users but OK for Admin"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by brawd on 2010-05-31
Hi all,

We're using Firefox 3.6.3(ish) and when the Mrs goes on the web there is no text. The home page is google.co.uk and we see the big GOOGLE bit but no other text.
A search, for say hotmail, seems to find a list in it's little drop down box but again there is no text. I swiped it with the mouse just in case the ink was the same colour as the paper, but nothing showed.

I made up another desktop user and got exactly the same thing - no text.
Googling the problem from my account showed up nothing at all. Nor could I find anything on the forums, but it's 4 am and I could easily have missed something.

The only things I've done recently is install a second hard drive and also the GeForce gt220 video card.

Anybody got any experience of this or some suggestions please. Any and all are gratefully received as we wish to stay in touch with the overseas offspring.

regards,

brawd.

---

### Post by lovinglinux on 2010-06-01
Normally I would suggest to create a new Firefox profile or start it in safe mode, but since you have already created a new desktop user, then I think this unnecessary, unless you have global extensions. Perhaps you could try to disable the Ubuntu Firefox Modifications extension and check if it solves the problem.

You could also try to copy the file prefs.js from your working profile to the new user to see if there is any difference. Also start Firefox from a terminal and check if you get any errors.

---

### Post by NUboon2Age on 2010-06-01
When you say 'OK for Adm' do you mean that you don't have this problem when you log in as root?

---

### Post by brawd on 2010-06-01
Sorry I'm a bit delayed but I had a few hours sleep.

Firefox for me as admin works perfectly.
I disabled all addons for my wife and it's still the same.
I then made her admin, (there's danger there I tell you), and it's still the same.

Then I typed the hotmail addy into the address bar and it went to the site but again no text.

brawd

---

### Post by brawd on 2010-06-01
I just remembered that when I installed 10.04 I had a few problems. From the word go I had problems. The half dozen disks I wrote all came up with an unrecoverable error. I got around that by selecting the 'Try first' option.

So I've just re-installed the whole shooting match, 70 minutes from start to finish -(you listening Microsoft?) and it all seems to work perfectly. i.e. The Mrs can now use Hotmail, Facebook........

I have no idea what caused it.

regards,

brawd.

---

### Post by brawd on 2010-06-02
I spoke too soon. This problem came back but this time nobody had text in Firefox. I had made a botch of installing some true type fonts but tried the fs-cache -f -v anyway. It was just after that the problem happened. I used my bookmarks to access other sites like this forum but they contained no text either.

I am a bit concerned about some hardware I installed. I replaced my old HDD with two new 500Gib HDDs and a graphics card. The HDDs seem to give out a lot of heat. I don't have a case fan and the computer is running nearly all day, every day. If there are thermal problems I would expect it to show up elsewhere but there's nothing I can put my finger on so far. No pun intended!

I did a fresh install again but this time I haven't installed the nVidia driver, I've just taken the default that comes with Ubuntu 10.04.

The only other stuff I've installed is Flash and Java.

We'll wait and see what happens over the next few days.

As for logging on as root well I have no idea how to do that. I will dabble on advice I'm given here but essentially me and my family are computer users and just install and use the programs we need which are the Internet browsers, social stuff like Skype and Facebook, and the photograph packages such as gthumb and gimp.

Any suggestions will be tried.

regards,

brawd.

---

### Post by lovinglinux on 2010-06-02
> **brawd said:**
> Firefox for me as admin works perfectly.

You are not starting Firefox with sudo are you?

If yes, then see the first item on [this list](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html).

---

### Post by brawd on 2010-06-02
Hi lovinglinux,

I don't start with sudo, just the icon at the top of the page. However I did read that tutorial and I think that a couple of solutions shown there are the answers to my intermittent problems. Anything is better than having to do a re-install, even if it is the quickest I've ever known.

For the time being I will continue to run without the nVidia drivers. When I feel on safe ground I'll add them in.

Thanking you,

brawd.

---

### Post by brawd on 2010-06-03
Right then,

I have something of a grip on this little problem. It occurred after I install my collection of fonts and somehow, even though my intention was to install fonts, it somehow prevented the default faults being available to desktop users.
By going to Edit, Preferences, Content and finally Advanced - where previously I had feared to tread - it allowed me to disable 'Allow pages to choose...' and nominate my own choice of font.

The font size seems to need tweaking as I don't know what font plays what part in the firefox page.
Not a big problem.

This has caused text to appear in firefox.

Anybody experienced this before?

regards,

brawd.

---

