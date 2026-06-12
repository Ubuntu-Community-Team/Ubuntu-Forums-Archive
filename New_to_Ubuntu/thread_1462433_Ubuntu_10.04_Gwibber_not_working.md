---
title: "Ubuntu 10.04 Gwibber not working"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by tonsil on 2010-04-25
I just did a clean install of Ubuntu 10.04 which is working fine. I set up my twitter account on Gwibber, however when I run it, it shows nothing, no timeline and can't send messages either. When I run it using terminal I get these:

** (gwibber:1883): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:1883): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:1883): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Updating...
Updating...
/usr/bin/gwibber:68: GtkWarning: gtk_container_add: assertion `GTK_IS_CONTAINER (container)' failed
  gtk.main()

** (gwibber:1883): CRITICAL **: murrine_style_draw_box: assertion `width >= -1' failed

Following these errors gwibber opens, but does not show anything. I uninstalled and re-installed gwibber but nothing changed. Is there anything I can do? Thanks! :)

---

### Post by tom.swartz07 on 2010-04-25
Its a known bug. Try looking here for more information: [https://bugs.edge.launchpad.net/gwibber/+bug/523964](https://bugs.edge.launchpad.net/gwibber/+bug/523964)

They should release an update soon. So far 43 other people have the problem.

---

### Post by curtiswtaylorjr on 2010-05-01
I setup my broadcast accounts and then opened gwibber all was well. But after a restart gwibber does not open nor does Broadcast Accounts from the Me Menu.

---

### Post by frederikbjerreandersen on 2010-05-01
I got the same problem - I can start Gwibber manually, but it doesn't start up automatically in the "Me Menu". Opening the list of accounts gives the message 'not connected - status offline' (or something, my language-setting is in danish...), which changes only when I manually open Gwibber.

---

### Post by Elie-M on 2010-05-01
well mine doesnt start at all. Displays same errors as the topic maker! so much for gwibber and social tryouts.

---

### Post by krishnandu.sarkar on 2010-05-01
Same problem. No updates is shown after setting up my twitter a/c. And one more problem. Gwibber, Empathy etc. doesn't startsup automatically after login.

---

### Post by quinnten83 on 2010-05-01
got the same issue with gwibber on UNE.

---

### Post by tom.swartz07 on 2010-05-01
I said this once before, but I guess it's worth repeating...

> **tom.swartz07 said:**
> Its a known bug. Try looking here for more information: [https://bugs.edge.launchpad.net/gwibber/+bug/523964](https://bugs.edge.launchpad.net/gwibber/+bug/523964)

They should release an update soon. So far 43 other people have the problem.



Go to lauchpad and (if you have an account) mark that it affects you also. It will put more pressure on the developers to fix the bug quicker. 



They also have a fix listed: [https://bugs.edge.launchpad.net/gwibber/+bug/523964/comments/17](https://bugs.edge.launchpad.net/gwibber/+bug/523964/comments/17)
Try following that- I dont know how it works, as I cant replicate this on my computer.

---

### Post by ubeautu on 2010-05-03
Ok, looking forward to the fix.

When I try to add my Facebook account I get to a box to associate gwibber with my fb account and then gwibber says that it is activated, but it does not get added to the accounts box on the left. It is just basically not adding accounts properly. (I'm using 32bit 10.04)

---

### Post by Felix-the-Cat on 2010-05-05
I think there are two bugs that people are experiencing.

Some people are able to get gwibber working by restarting gwibber-services as reported here: [https://bugs.edge.launchpad.net/gwibber/+bug/523964](https://bugs.edge.launchpad.net/gwibber/+bug/523964)

Other people (including me) cannot get gwibber running period. Ther are no gwibber-services to restart. That has been reported here: [url]https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/575461[/url/

Hope this helps.

---

### Post by woop on 2010-05-19
fix is badly needed for this.......its one of the main selling points which 10.04 was debuted with

yeh I know it isnt technicallly for sale, but it should work

there are 2 bugs here krishnandu.sakar reffered to the one Im experiencing. Neither empathy or qwibber auto starts and gwibber doesnt work at all. I can add twitter and flickr but neither shows up under qwibber and Fb as shown in the attached image in this thread cant be "add" to stream despite being "authorised"

any find a fix?

---

### Post by Greblok on 2010-05-24
Since there seems to be two different issues with Gwibber, I'm going to post the solution i found by myself on one of the issues:[B]
Gwibber (and Ubuntu One) not starting, no service to restart.[/B]

The solution I found was so simple I was embarrassed. :P

I had disabled password request upon login to Ubuntu. Once I enabled the login prompt all was fine and working well again. 
I also have disabled login at user switch and screen saver resume, but those do not appear to affect the Gwibber service at all.

Maybe this simple solution could help someone else. :)

---

### Post by sw34963 on 2010-05-25
found this fix at [https://bugs.edge.launchpad.net/gwibber/+bug/523964]("https://bugs.edge.launchpad.net/gwibber/+bug/523964")
responce #30.

It states to 
> start gnome-keyring-daemon from terminal and the start gwibber again
it should work then

I did this and I went from gwibber not working at all to fully functioning.

Although I havent restared yet,  may have to do this each time untill a fix is found.

---

### Post by jbruni on 2010-05-25
Not sure if this is related, but it may be:

[http://ubuntuforums.org/showthread.php?p=9359196#post9359196](http://ubuntuforums.org/showthread.php?p=9359196#post9359196)

---

### Post by Slochez on 2010-06-04
I finally found a solution for some of the problems. i wasn´t able to authorize facebook and twitter wasn´t working. After weeks of googling, reinstalling etc. I finally found a post that mentioned that it might be related to your dns-server. After changing the dns-server to a us-based ( I live in germany ) in my connection-settings ( I use ethernet with a manually applied ip ) I was able to recieve and send twitter-postings and complete the facebook authorisation, I´m able to post on facebook via gwibber, what still doesn´t work is that I´m unable to see any updates on my profile through gwibber. Hope this helps you at least a little

---

### Post by kindofabuzz on 2010-06-04
Gwibber just plain sucks. Slow, bloated, and unresponsive at times. Pino is a much better choice.

---

### Post by LancerNZ on 2010-06-04
> **kindofabuzz said:**
> Gwibber just plain sucks. Slow, bloated, and unresponsive at times. Pino is a much better choice.

I agree - the current implementation of Gwibber into Ubuntu is one of the biggest disasters I've ever seen on Linux. It simply does not work... what were they thinking to have it as an "in your face" default app?

As for Pino - do you have any plain english and simple steps to install?

So far I have added _*their*_ repositories (looking at the steps from the pino page I found on google), and yet pino does not show up even after an apt refresh.

Then I added cmake...
Then I added hg...

....all of this just for pino (I'm getting really annoyed now that just wanting a frigging facebook/twitter client is turning out to be such a long winded route for bloating my system)....

...and it still fails to build... can't find "Vala"?!?

```
lancer@lancer-laptop:~/pino-twitter/build$ cmake ../ -DCMAKE_INSTALL_PREFIX=/usr -DUBUNTU_ICONS=OFF -DENABLE_DEBUG=OFF
CMake Error at /usr/share/cmake-2.8/Modules/FindPackageHandleStandardArgs.cmake:70 (MESSAGE):
  Could NOT find Vala (missing: VALA_EXECUTABLE)
Call Stack (most recent call first):
  cmake/FindVala.cmake:55 (find_package_handle_standard_args)
  cmake/ValaVersion.cmake:31 (find_package)
  CMakeLists.txt:38 (include)


-- Configuring incomplete, errors occurred!
```

I don't think Ubuntu is ready for Twitter / Facebook.

---

### Post by kindofabuzz on 2010-06-04
> **LancerNZ said:**
> I agree - the current implementation of Gwibber into Ubuntu is one of the biggest disasters I've ever seen on Linux. It simply does not work... what were they thinking to have it as an "in your face" default app?

As for Pino - do you have any plain english and simple steps to install?

So far I have added _*their*_ repositories (looking at the steps from the pino page I found on google), and yet pino does not show up even after an apt refresh.

Then I added cmake...
Then I added hg...

....all of this just for pino (I'm getting really annoyed now that just wanting a frigging facebook/twitter client is turning out to be such a long winded route for bloating my system)....

...and it still fails to build... can't find "Vala"?!?

```
lancer@lancer-laptop:~/pino-twitter/build$ cmake ../ -DCMAKE_INSTALL_PREFIX=/usr -DUBUNTU_ICONS=OFF -DENABLE_DEBUG=OFF
CMake Error at /usr/share/cmake-2.8/Modules/FindPackageHandleStandardArgs.cmake:70 (MESSAGE):
  Could NOT find Vala (missing: VALA_EXECUTABLE)
Call Stack (most recent call first):
  cmake/FindVala.cmake:55 (find_package_handle_standard_args)
  cmake/ValaVersion.cmake:31 (find_package)
  CMakeLists.txt:38 (include)


-- Configuring incomplete, errors occurred!
```

I don't think Ubuntu is ready for Twitter / Facebook.

easy
```
sudo add-apt-repository ppa:troorl/pino && sudo apt-get update && sudo apt-get install pino 
```

I really like Pino, but just found out about Turpial. Even better!! [http://www.omgubuntu.co.uk/2010/05/turpial-in-english-finally-comes-to-ppa.html](http://www.omgubuntu.co.uk/2010/05/turpial-in-english-finally-comes-to-ppa.html)

---

### Post by LancerNZ on 2010-06-04
Thanks. I'd just managed to install manually though (I had overlooked a whole host of dependencies at the bottom of the pino page) as after updating my repos it seemed like the package pino still couldn't be found. Odd though - now it is... mush have got the update wrong or something, but it is working. Will look at the other one you mention as well.

Thanks.

P.S. Gwibber still sucks - I vote they get rid of it from Ubuntu.

---

### Post by LancerNZ on 2010-06-04
Trupial looks good but it freezes when typing in the authentication code. I have to kill it as a process. Then it asks for an authentication all over again when I run it the next time. Can't get beyond that.

---

### Post by Zer0Nin3r on 2010-06-08
> **tom.swartz07 said:**
> I said this once before, but I guess it's worth repeating...





Go to lauchpad and (if you have an account) mark that it affects you also. It will put more pressure on the developers to fix the bug quicker. 



They also have a fix listed: [https://bugs.edge.launchpad.net/gwibber/+bug/523964/comments/17](https://bugs.edge.launchpad.net/gwibber/+bug/523964/comments/17)
Try following that- I dont know how it works, as I cant replicate this on my computer.


:lolflag: If only there were an easy button for everyone.  I do like the launchpad feature of marking "This affects me" versus subscribing to each bug.

---

### Post by o1e9 on 2010-06-09
... and feed those bug activities to gwibber.

---

### Post by Flash858 on 2010-06-15
Gwibber isn't worth the bug report. I have had the same issues with it simply not working. All I get is a blank window, no updates, no history, nothing. I can't add Facebook, even though Facebook sees it, and everything is allowed.

sudo apt-get remove gwibber && sudo apt-get autoremove seemed to do the trick though...

---

### Post by voodoostevie on 2010-06-16
I'm having the same issue after I just finished doing a full reinstall and updates Gwibber not only is not allowing Facebook to be added, but FriendFeed doesn't show in the accounts screen after I added it. It allowed Twitter and Identica to be added but that was it.

Also the quick broadcast in the Me Menu has gone missing as well.

One thing I noticed is that if you add the PPA for Gwibber dailies this causes the Me Menu to become quirky. I noticed this when I had my machine on a dual boot (Win 7 / Ubuntu) but since the fresh reinstall I did not add it and it's still gone. BAH!

---

### Post by gsiliceo on 2010-06-27
OUt of the box is not working gwibber sucks i'll try pino

---

### Post by krishnandu.sarkar on 2010-06-27
Guys leave Gwibber use TweetDeck. Check it out. Its awesome. I'm sure you'll like it. It also comes with Facebook, Google Buzz, MySpace, LinkedIn etc. Geo-Tagging is also possible :)

---

### Post by exodust on 2010-07-20
I'm also having this problem.

I think I'll do fine with waiting and doing what I can to help to fix Gwibber (or whatever program is chosen to be embedded into the current/future releases of Ubuntu).

---

### Post by donato roque on 2010-07-24
If you are running Ubuntu 10.04 I think you should stick with the main repositories.  By this you should not add the ppa's...at least for Gwibber.

---

### Post by krishnandu.sarkar on 2010-07-24
Well...Gwibber is fixed now..after this update. It's working fine for me now.

---

### Post by awi on 2010-08-09
I'm using Ubuntu 10.04, Gwibber stopped working for me on Aug 05, I use it for tweeter and facebook, and both are not working. I'm fully updated. I'm getting this errors when running from a terminal, but I don't see any account problem related in this output:
```

** (gwibber:29053): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (gwibber:29053): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (gwibber:29053): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Updating...
Updating...
/usr/bin/gwibber:68: GtkWarning: IA__gtk_container_add: assertion `GTK_IS_CONTAINER (container)' failed
  gtk.main()

```

---

### Post by rebecacaca on 2010-08-16
I found a hint for a solution via [bug 523327]("https://bugs.launchpad.net/ubuntu/+source/python-httplib2/+bug/523327").

Basically, check your /etc/hosts file ("sudo gedit /etc/hosts" into a terminal window to open) has the following:

127.0.0.1 localhost
127.0.1.1 your computer name

Mine had "username-laptop" where it should have had "your computer name". After changing this it works perfectly.

---

### Post by Flash858 on 2010-08-26
I must apologize to the Gwibber community and its developers. After adding the daily builds to the repositories, it is now working like a charm (dare I say it is Magical and revolutionary?).

Facebook updates are still a bit slow, and I do wish they would add Linkedin, but I can say that I now no longer have to run TweetDeck, and the exceedingly icky Adobe Air, which just made me feel dirty every time I used it...

Well done Gwibber Team!

---

### Post by Pilot824 on 2011-03-24
Sorry for being so noobish, but how do you add the daily builds?

> **Flash858 said:**
> I must apologize to the Gwibber community and its developers. After adding the daily builds to the repositories, it is now working like a charm (dare I say it is Magical and revolutionary?).

Facebook updates are still a bit slow, and I do wish they would add Linkedin, but I can say that I now no longer have to run TweetDeck, and the exceedingly icky Adobe Air, which just made me feel dirty every time I used it...

Well done Gwibber Team!

---

