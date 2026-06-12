---
title: "simple question about firefox"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by heyyy on 2009-07-02
i have shiretoko but recently i downloaded firefox 3.5 from mozilla website.
what the difference?
if i install the firefox from mozilla will it be a newer version?
also will i have the upgrade button?

---

### Post by WRDN on 2009-07-02
For the new and improved aspects in Firefox 3.5, read the [Release Notes]("http://www.mozilla-europe.org/en/firefox/3.5/releasenotes/").

It is the newer version, as Firefox 3.5 isn't available in the repositories yet.

Also, Firefox will not get updates from the Update-Manager. For this to happen, you need to install through the repositories. The alternative is to use the "Check for Updates" option under the Help menu occasionally.

---

### Post by heyyy on 2009-07-02
> **WRDN said:**
> For the new and improved aspects in Firefox 3.5, read the [Release Notes]("http://www.mozilla-europe.org/en/firefox/3.5/releasenotes/").

It is the newer version, as Firefox 3.5 isn't available in the repositories yet.

Also, Firefox will not get updates from the Update-Manager. For this to happen, you need to install through the repositories. The alternative is to use the "Check for Updates" option under the Help menu occasionally.

ok thanks
could you point me in some instructions on how to install from the
firefox-3.5.tar.bz2 file?

---

### Post by frunns on 2009-07-02
I suppose it's like, unpack it (just double click and figure it out) and then in the root of the folder you just do:
./configure
make
sudo make install

However, there could be a readme in the folder, so check that out! :)

---

### Post by WRDN on 2009-07-02
I've just looked in Synaptic, and apparently it is there (firefox-3.5). My bad. Note that, Canonical do not provide updates for it.

I've just taken a look at the bzip2 archive, and it contains the binaries, so there is no need to run ./configure or make install.
I would recommend installing from the repositories however, because it will automatically install unmet dependencies.

---

### Post by alphacrucis2 on 2009-07-02
> **frunns said:**
> I suppose it's like, unpack it (just double click and figure it out) and then in the root of the folder you just do:
./configure
make
sudo make install

However, there could be a readme in the folder, so check that out! :)

Actually I think that archive you download from Mozilla is the binaries, already compiled. You just extract and run it.

---

### Post by Bölvaður on 2009-07-02
For constant updates you will have to have the program installed through repositories (almost always shortened to repos). When you install in any other way you will have to maintain what you install your self.

This is how you can add the latest firefox to your repos ([SIZE=1]PPA for Ubuntu Mozilla Daily Build Team[/SIZE] (where PPA stands for Personal Package Archives))

Click this link:

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa")

Look for: "Display sources.list entries for: "
and pick the release you have, I have 9.04 so I have to use Jaunty. And then copy the first line in the "code box" (looks somehting like this: deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main)

Then go to the menu that might be on top of your screen.
System &#8594; Administration &#8594; Software Sources

Click Third party Software
Click +Add...
Paste the code into the box

Do not panic if you see it complain about it being authenticated or doesnt have the correct key. That is our next job, to add the key. The key tells us that the software from the repo has not been fittled with by third party... like people that put virus in it, so the key is your friend.

Look at the website again and see:
Signing key:                            [                 1024R/247510BE               ]("http://keyserver.ubuntu.com:11371/pks/lookup?search=0xB34505EA326FEAEA07E3618DEF4186FE247510BE&op=index")               ([What is this?]("https://launchpad.net/+help/soyuz/ppa-sources-list.html"))             

Click on the number. And again on the number (/[247510BE]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xEF4186FE247510BE"))

Now copy everything from 
-----BEGIN PGP PUBLIC KEY BLOCK-----
to
-----END PGP PUBLIC KEY BLOCK-----

Including those 2 lines.


Now we have to paste this in an emtpy file.
Let's create one on the desktop and paste the key code into it.

A quick way to do that is hold down ctrl+alt and press right or left arrow on your keyboard.
Right click your desktop and select Create document &#8594; Emtpy file
Double click it and paste your code
Save and close it.

Open Software Sources again and

Click : Aunthentication
Click : +Import Key file..
Browse to your desktop and select your new file.


After doing this it is ok to delete the file.
You can open Synaptic Package manager to install firefox now. You can filter it by selecting Origin instead of Sections and select the ppa.launchpad.net/universe

---

### Post by heyyy on 2009-07-02
i found a link [here]("http://www.1earthadventures.com/2009/07/01/the-net-now/installing-firefox-3-5-tar-bz2-on-ubuntu-9-04/") on how to install
should i follow this or not?

---

### Post by frunns on 2009-07-02
> **alphacrucis2 said:**
> Actually I think that archive you download from Mozilla is the binaries, already compiled. You just extract and run it.

Yeah, my bad. I'd go for Bölvaður's explanation, if you really want the latest, otherwise just go for the usual one in the repo, as it seems to be 3.5 now as well.

---

### Post by heyyy on 2009-07-02
> **Bölvaður said:**
> For constant updates you will have to have the program installed through repositories (almost always shortened to repos). When you install in any other way you will have to maintain what you install your self.

This is how you can add the latest firefox to your repos ([SIZE=1]PPA for Ubuntu Mozilla Daily Build Team[/SIZE] (where PPA stands for Personal Package Archives))

Click this link:

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa")

Look for: "Display sources.list entries for: "
and pick the release you have, I have 9.04 so I have to use Jaunty. And then copy the first line in the "code box" (looks somehting like this: deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main)

Then go to the menu that might be on top of your screen.
System &#8594; Administration &#8594; Software Sources

Click Third party Software
Click +Add...
Paste the code into the box

Do not panic if you see it complain about it being authenticated or doesnt have the correct key. That is our next job, to add the key. The key tells us that the software from the repo has not been fittled with by third party... like people that put virus in it, so the key is your friend.

Look at the website again and see:
Signing key:                            [                 1024R/247510BE               ]("http://keyserver.ubuntu.com:11371/pks/lookup?search=0xB34505EA326FEAEA07E3618DEF4186FE247510BE&op=index")               ([What is this?]("https://launchpad.net/+help/soyuz/ppa-sources-list.html"))             

Click on the number. And again on the number (/[247510BE]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xEF4186FE247510BE"))

Now copy everything from 
-----BEGIN PGP PUBLIC KEY BLOCK-----
to
-----END PGP PUBLIC KEY BLOCK-----

Including those 2 lines.


Now we have to paste this in an emtpy file.
Let's create one on the desktop and paste the key code into it.

A quick way to do that is hold down ctrl+alt and press right or left arrow on your keyboard.
Right click your desktop and select Create document &#8594; Emtpy file
Double click it and paste your code
Save and close it.

Open Software Sources again and

Click : Aunthentication
Click : +Import Key file..
Browse to your desktop and select your new file.


After doing this it is ok to delete the file.
You can open Synaptic Package manager to install firefox now. You can filter it by selecting Origin instead of Sections and select the ppa.launchpad.net/universe

thamks a lot 
i've done that but one more question
on the application menu it says minefield 3.5
and when i open the browser it still says shiretoko on the top
is this how it supposed to be?

---

### Post by frunns on 2009-07-02
> **heyyy said:**
> thamks a lot 
i've done that but one more question
on the application menu it says minefield 3.5
and when i open the browser it still says shiretoko on the top
is this how it supposed to be?

It says Shiretoko when you open the app that says Minefield? It probably shouldn't...

---

### Post by heyyy on 2009-07-02
> **frunns said:**
> It says Shiretoko when you open the app that says Minefield? It probably shouldn't...

i does actually 
can someone help me understand?

---

### Post by frunns on 2009-07-02
> **heyyy said:**
> i does actually 
can someone help me understand?

But if you go to, in the browser, help->About Minefield/Shiretoko/Mozilla Firefox (whatever it says... :P). What does it say there?

---

### Post by heyyy on 2009-07-02
> **frunns said:**
> But if you go to, in the browser, help->About Minefield/Shiretoko/Mozilla Firefox (whatever it says... :P). What does it say there?

its says "about shiretoko"

---

### Post by frunns on 2009-07-02
> **heyyy said:**
> its says "about shiretoko"

Okay, I actually was going for what it said if you clicked that option, but whatever, probably says that it's shiretoko you're anyway. I guess it's a symbolic link somewhere that's off...

---

### Post by caravel on 2009-07-02
To clarify:

v3.0 = Gran Paradiso
v3.5 = Shiretoko
V3.6 = Namoroka

If you have a "Minefield" build that means you have an unstable build.  So in a nutshell you should upgrade to Firefox v3.5

---

### Post by frunns on 2009-07-02
> **caravel said:**
> To clarify:

v3.0 = Gran Paradiso
v3.5 = Shiretoko
V3.6 = Namoroka

If you have a "Minefield" build that means you have an unstable build.  So in a nutshell you should upgrade to Firefox v3.5

Oh crap. I had no idea. I just figured he had some weird build, didn't look into it...

---

### Post by Razmear on 2009-07-02
Will the update manager update firefox 3.0.x to firefox 3.5 in a few days once testing is done, or do I have to install firefox 3.5 from the repos to get the updated version? 

Thanks,
eb

---

### Post by heyyy on 2009-07-02
> **Razmear said:**
> Will the update manager update firefox 3.0.x to firefox 3.5 in a few days once testing is done, or do I have to install firefox 3.5 from the repos to get the updated version? 

Thanks,
eb

i would like also to know this

---

