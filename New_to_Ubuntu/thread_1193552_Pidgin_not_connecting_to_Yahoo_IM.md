---
title: "Pidgin not connecting to Yahoo IM"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by diablo75 on 2009-06-21
I've been using Pidgin for a few years under Ubuntu and really haven't ever had any big problems with it.  I'm just tossing this out to see if anyone else has had this happen to them within the last week or so.

I'll start Pidgin and it will attempt to auto connect to Yahoo, but the connection just hangs.  The program doesn't lock up for produce any errors.  It just looks like the picture I've attached (see below) forever.  I've attempted many reconnection as well as deleting the account from my account manager and re-adding it, but that didn't help.  I also tried reinstalling Pidgin via Synaptic and that didn't help either.

So not sure what I should try next.  Any suggestions?  I'd even be happy with an alternate IM client as long as it works with Yahoo.

---

### Post by desperado665 on 2009-06-21
This post should answer all your questions.

[http://www.celticwolf.com/useful-information/faqs/26-pidgin-yahoo]("http://www.celticwolf.com/useful-information/faqs/26-pidgin-yahoo")

---

### Post by drs305 on 2009-06-21
Note Added: The update to Pidgin 2.5.7 as of 24 June 2209 makes this step unnecessary and the "Page server" window should remain as "scs.msg.yahoo.com".

Original Post:
Referencing the previously provided link, I was successful by using: 66.163.181.170 instead of "scs.msg.yahoo.com" in the Advanced tab, "Pager server" window.

Added: Yes, this is widespread problem and has been happening often recently.

---

### Post by Thelasko on 2009-06-21
> **diablo75 said:**
> I've been using Pidgin for a few years under Ubuntu and really haven't ever had any big problems with it.  I'm just tossing this out to see if anyone else has had this happen to them within the last week or so.

Yeah, I had this too.  I just assumed it was on Yahoo's end.

---

### Post by LewRockwell on 2009-06-21
seems yahoo has been messing around with their stuff

[http://bigbrovar.wordpress.com/2009/06/21/how-to-fix-pidgin-and-yahoo-issues/](http://bigbrovar.wordpress.com/2009/06/21/how-to-fix-pidgin-and-yahoo-issues/)

---

### Post by diablo75 on 2009-06-22
> **drs305 said:**
> Referencing the previously provided link, I was successful by using: 66.163.181.170 instead of "scs.msg.yahoo.com" in the Advanced tab, "Pager server" window.

Added: Yes, this is widespread problem and has been happening often recently.

Awesome, that did the trick!  Thanks!

---

### Post by drs305 on 2009-06-24
> **diablo75 said:**
> Awesome, that did the trick!  Thanks!

Just an update: This morning yahoo failed to respond with the new address I provided in post #3. I subsequently restored "scsc.msg.yahoo.com" in the 'pager server' block and it successfully connected. I am now using Pidgin 2.5.7 and the default entries appear to be working again.

This site appears to be keeping on top of things:
[http://www.celticwolf.com/useful-information/faqs/26-pidgin-yahoo]("http://www.celticwolf.com/useful-information/faqs/26-pidgin-yahoo")

---

### Post by Georgia boy on 2009-06-24
I've tried them all this morning. Still can't get pidgin to accept me. Each time I log in and click on show buddy list it shows that I'm disconnected even though there is a green circle showing that I'm available at the top of the browser. It says: "Could not establish a connection with the server. Connection refused".
I'm using the pidgin from the repos in Hardy 8.04. 
Any ideas as to what to use now?
Thanks
Tom

---

### Post by squishy121888 on 2009-06-24
> **Georgia boy said:**
> I've tried them all this morning. Still can't get pidgin to accept me. Each time I log in and click on show buddy list it shows that I'm disconnected even though there is a green circle showing that I'm available at the top of the browser. It says: "Could not establish a connection with the server. Connection refused".
I'm using the pidgin from the repos in Hardy 8.04. 
Any ideas as to what to use now?
Thanks
Tom


Open the terminal add this:


sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
 echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list



Next open synaptic, and search for pidgin 2.5.7, and install that as an upgrade. That's what fixed it for me.

---

### Post by diablo75 on 2009-06-25
> **squishy121888 said:**
> Next open synaptic, and search for pidgin 2.5.7, and install that as an upgrade. That's what fixed it for me.

Actually it appears to upgrade this (after executing that code in a terminal window) if you just run Update Manager instead of Synaptic.  Just be sure the page server is "scsc.msg.yahoo.com" and not that IP address.

---

### Post by Georgia boy on 2009-06-25
Actually, this morning I used the following:
cn.scs.msg.yahoo.com
Guess I'll keep an eye on it a few days and see how it goes. If it acts up again I'll go ahead and try the install of the newer verson.
By the way, when is the next LTS due out? I can't remember.
Thanks
Tom

---

### Post by misswham on 2009-06-26
I have upgraded to the new version and it connected day before yesterday then that night when i double clicked the icon it would connect and immediately shut off.  Not disconnect my connection, the whole thing would cut off and disappear from the tool bar as if i clicked on quit.  that is the problem i am having now, not the connecting its staying ON.

---

### Post by sandalgod on 2009-06-27
> **Georgia boy said:**
> Actually, this morning I used the following:
cn.scs.msg.yahoo.com
Guess I'll keep an eye on it a few days and see how it goes. If it acts up again I'll go ahead and try the install of the newer verson.


im using the same and its working for now. i'll keep an eye on it too.  thanks for the iggy

---

### Post by Thelasko on 2009-06-27
> **Georgia boy said:**
> Actually, this morning I used the following:
cn.scs.msg.yahoo.com

Worked for me too.

Thanks!

---

### Post by Georgia boy on 2009-06-27
I can't take full credit for what I'm using. Found it in another post in the forum after having tried the various IP addresses only to have them work for a bit then quit on me. Kept researching and came across that one. I don't know where it comes from but seems to be working so far. At least my buddy list comes up and I stay signed on so far. Don't know if I want to upgrade to the newer version or not. Saw where someone in this post did that and still seemed to have some problems. I notice that when I do go and open the terminal I see my name, computer name and some other stuff. If I do decide to upgrade to the newer version of Pidgin would I just copy that and put it in under that heading and hit enter? Sorry, know stupid question but only used terminal once when I first started and had some problem and someone had me check something out in the terminal for them. That was awhile back. 
Also, any idea when the next LTS is due out and should it have all the updated versions of OpenOffice.org, Pidgin etc?
Thanks everyone
Tom

---

### Post by RD1 on 2009-06-27
Upgrade to new version 2.5.7

Delete your yaHoo account from pidgin and recreate it.

---

### Post by Georgia boy on 2009-06-27
> **squishy121888 said:**
> Open the terminal add this:


sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
 echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list



Next open synaptic, and search for pidgin 2.5.7, and install that as an upgrade. That's what fixed it for me.


Okay, I did a copy and paste of this and put it in the terminal as one paste. Here is what I got:

thomas@Thriller:~$ 
thomas@Thriller:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \ 67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
[sudo] password for thomas: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com  67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
gpg: requesting key A1F196A8 from hkp server keyserver.ubuntu.com
gpg: key A1F196A8: public key "Launchpad PPA for Pidgin Developers" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
thomas@Thriller:~$ 
When I went to the update manager nothing happened.
Was I supposed to paste all of that in the terminal at one time or did I miss understand and mess up when I did that?  
It's working with the scs.msg.yahoo.com but when I do a check in the about it gives the 2.4.1 version. So, somehow something didn't work as advertised?  Please advise.
Thanks
Tom

---

### Post by drs305 on 2009-06-27
Georgia boy,

After you imported the key (sudo apt-key adv --recv...) you have to run the next two lines (as one command) as well.

The second two lines ([B]echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \ `lsb_release --short --codename` main | \
sudo tee /etc/apt/sources.list.d/pidgin-ppa.list[/B]) are actually one long single command. It adds the new repository to your source lists.

Then run "sudo apt-get update" to update the repositories. You should then be able to upgrade pidgin via the command line or synaptic.

---

### Post by Georgia boy on 2009-06-27
YEAH Team!!!!!!!!!!!
Hi guys and gals!!! I did it. I actually went to the Pidgin site and did a copy and paste of what they had into the terminal. I think that I had screwed up the first time when I did it by doing a copy and paste out of this post. I had put everything into the terminal at once. When I had gone to the site tried I noticed that I could only copy and paste one at a time. So that's what I did and then went back into the Synaptic and pulled it in that way. It pulled the updates in and now I have the 2.5.7 version. 

Thanks everyone for their patience with an "Old Windows" user. Figuring that I had started out learning to use a computer in a collage class in DOS then Windows 3.1 and from then on it was completely Windows all the way. Glad that I found Ubuntu and installed it, though I am using a dual boot. Think that when the next LTS comes out I'll wipe out Windows completely. Of course I'll be researching the forum hard then making sure that I don't mess that up. But I'll still be learning every time I turn on the computer since I automatically boot to Ubuntu and only use Windows if I have to go back to answer something for someone if I can't remember it automatically. 

Yes you can teach an old dog new tricks.Just look at me.:wink: Look at some of the questions I have asked. I'm always reading in the forums and trying to learn and I appreciate all the help I get every time I have to ask something that I can't find the answer to that will work for me.

Again, I thank you for your patience and help.
Tom

---

### Post by rbulalakaw on 2009-06-28
> **Georgia boy said:**
> Actually, this morning I used the following:
cn.scs.msg.yahoo.com
Guess I'll keep an eye on it a few days and see how it goes. If it acts up again I'll go ahead and try the install of the newer verson.
By the way, when is the next LTS due out? I can't remember.
Thanks
Tom

I have Ubuntu 9.04, Pidgin 2.5.5. this resolution helped me every time. I might upgrade to 2.5.7, though. what are the changes?

Thanks!

---

### Post by Georgia boy on 2009-06-30
Haven't noticed that much difference then again others might. I do know that there is file transfer problems. I can send files like jpeg but when my niece tried to send to me I couldn't receive them. They say that the newer 2.5.8 takes care of that. But does the update manager automatically take care of doing that for us or do we have to manualy do the update ourselves?

Tom

---

### Post by drs305 on 2009-06-30
> **Georgia boy said:**
> They say that the newer 2.5.8 takes care of that. But does the update manager automatically take care of doing that for us or do we have to manualy do the update ourselves?

Tom

The newer version most likely won't be placed into the official Ubuntu repositories. Ubuntu is not a 'rolling release' so new versions of applications are normally only introduced with a new release of Ubuntu (hardy, jaunty, karmic, etc). 

You can add third party repositories which will provide updates when the newer versions become available (if the app is registered with APT - via an install by synaptic, apt-get, aptitude, etc).

The pidgin repository is:
[http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) 
Put this into Synaptic, along with your release (jaunty) and *main*

---

### Post by thatDougore on 2009-07-01
I had a similar problem and was finally able to connect by changing the port to 80. Hope this helps.

./Doug

---

### Post by mickey12gauge on 2009-07-16
> **thatDougore said:**
> I had a similar problem and was finally able to connect by changing the port to 80. Hope this helps.

./Doug



:popcorn:Thanks a lot, changing the port to 80 helped me out... Finally fixed ;):popcorn:

---

### Post by pvfjr on 2009-07-17
Upgrading to 6.5.8 just fixed my problems, used all the default settings.

---

### Post by brmc on 2009-07-31
yahoo people must have changed their server settings

so just change advance settings
replace scsa.msg.yahoo.com with  scs.msg.yahoo.com
then it should be ok
or u can install pidgin 2.5.8
if u wana update your exciting pidgin,
simply run these in terminal

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8

 echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list
   
then run the update manager 

if u need more assistance 
go to : [http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)

chinthaka bandara

---

### Post by Thelasko on 2009-08-18
Well the fix I used just quit working.  I guess I will have to upgrade:(  Any chance the newest version of Pidgin will be backported to Hardy?

[I guess the developers haven't decided yet.]("https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/389322")

---

