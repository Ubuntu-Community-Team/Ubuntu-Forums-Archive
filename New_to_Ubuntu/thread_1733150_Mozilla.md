---
title: "Mozilla"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by jiggajoe506 on 2011-04-18
I tried being a superstar and downloading the new mozilla and installing it through command and it does not work properly anymore. So i tried to uninstall it and reinstall it but i get the message in the photo. Any easy ubuntu brain dead dead help. thanks for your help in advance from your help guys. Excited to be in the community.

---

### Post by wojox on 2011-04-18
What command and what picture?

---

### Post by dFlyer on 2011-04-18
> **jiggajoe506 said:**
> I tried being a superstar and downloading the new mozilla and installing it through command and it does not work properly anymore. So i tried to uninstall it and reinstall it but i get the message in the photo. Any easy ubuntu brain dead dead help. thanks for your help in advance from your help guys. Excited to be in the community.

What message, what photo. What command line command did you use to install and uninstall the program????

---

### Post by Frogs Hair on 2011-04-18
We need the photo please .;-)

---

### Post by jiggajoe506 on 2011-04-18
haha sorry guys it didn't upload thanks for the speedy responses! you guys are awesome!

---

### Post by sandyd on 2011-04-18
> **jiggajoe506 said:**
> haha sorry guys it didn't upload thanks for the speedy responses! you guys are awesome!

I really hope your using ubuntu 10.10

```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:ubuntu-mozilla-daily/ppa

```Did you install this thingy? -> [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa")

by any chance?****
If yes, run the above,.

---

### Post by jiggajoe506 on 2011-04-19
> **sandyd said:**
> I really hope your using ubuntu 10.10

```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:ubuntu-mozilla-daily/ppa

```Did you install this thingy? -> [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa")

by any chance?****
If yes, run the above,.

No I don't think I did... and yes i am running 10.10

this unrelated to the mozilla issue but my wireless when using ubuntu at home will not work at all but when i fire up windows it does.

---

### Post by lovinglinux on 2011-04-19
Please run the following commands and then copy/paste the contents of firefox-report.txt file created in your Desktop.

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by jiggajoe506 on 2011-04-19
> **lovinglinux said:**
> Please run the following commands and then copy/paste the contents of firefox-report.txt file created in your Desktop.

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

I did it and it took me to [www.stall.com?](www.stall.com?) then nothing happened

---

### Post by lovinglinux on 2011-04-19
> **jiggajoe506 said:**
> I did it and it took me to [www.stall.com?](www.stall.com?) then nothing happened

Look in your desktop. It should be a *firefox-report.txt* file there. Open it, copy the contents and paste here.

---

### Post by ClientAlive on 2011-04-19
* _jiggajoe_ - Are you using a Macintosh machine? I noticed the apple icon on the corner of the window in one of your pictures. Not sure how much of a difference that observation makes but I thought I should share it.

Thanks
Jake

---

### Post by jiggajoe506 on 2011-04-19
ok Idk how you make those little box things but heres what the file has on the desktop:


[B]Ubuntu Architecture

Linux joey-Aspire-5551 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

Firefox Packages

firefox						deinstall
firefox-4.0					install
firefox-trunk					install
firefox-trunk-globalmenu			install

Firefox binaries

/home/joey/bin/firefox
/usr/bin/firefox: ERROR: cannot open `/usr/bin/firefox' (No such file or directory)
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: directory

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

bisigi-ppa-maverick.list
bisigi-ppa-maverick.list.save
dropbox.list
dropbox.list.save
medibuntu.list
medibuntu.list.save
tiheum-equinox-maverick.list
tiheum-equinox-maverick.list.save
ubuntu-mozilla-daily-ppa-maverick.list
ubuntu-mozilla-daily-ppa-maverick.list.save
ubuntu-tweak-stable.list
ubuntu-tweak-stable.list.save
[/B]

---

### Post by lovinglinux on 2011-04-19
> **jiggajoe506 said:**
> ok Idk how you make those little box things but heres what the file has on the desktop:


```
Ubuntu Architecture

Linux joey-Aspire-5551 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

Firefox Packages

firefox						deinstall
firefox-4.0					install
firefox-trunk					install
firefox-trunk-globalmenu			install

Firefox binaries

/home/joey/bin/firefox
/usr/bin/firefox: ERROR: cannot open `/usr/bin/firefox' (No such file or directory)
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: directory

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

bisigi-ppa-maverick.list
bisigi-ppa-maverick.list.save
dropbox.list
dropbox.list.save
medibuntu.list
medibuntu.list.save
tiheum-equinox-maverick.list
tiheum-equinox-maverick.list.save
ubuntu-mozilla-daily-ppa-maverick.list
ubuntu-mozilla-daily-ppa-maverick.list.save
ubuntu-tweak-stable.list
ubuntu-tweak-stable.list.save

```

First, to put code inside a box like above, just put the **[noparse]```
TEXT
```[/noparse]** tags around the text. there is a button (**#**) in the forum text editor toolbar that do that for you.

About your Firefox problem, you are using a unstable channel.
Go to "System >>> Administration >> Software Sources >> Other Software" and remove the lines that contains:
```

http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu maverick main
```

Then run these from a terminal:

```
sudo apt-get update
sudo apt-get purge firefox-4.0
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get install firefox

```

These will purge your unstable Firefox 4 installation and install the stable Firefox 4 version from mozillateam firefox-stable ppa.

Keep in mind that thew repository you was using probably cloned your Firefox profile folder **~/.mozilla/firefox** to **~/.mozilla/firefox-4.0**. So if you miss something like recent saved bookmarks or passwords, you might need to import them them from the cloned profile.

---

### Post by jiggajoe506 on 2011-04-19
> **lovinglinux said:**
> First, to put code inside a box like above, just put the **[noparse]```
TEXT
```[/noparse]** tags around the text. there is a button (**#**) in the forum text editor toolbar that do that for you.

About your Firefox problem, you are using a unstable channel.
Go to "System >>> Administration >> Software Sources >> Other Software" and remove the lines that contains:
```

http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu maverick main
```

Then run these from a terminal:

```
sudo apt-get update
sudo apt-get purge firefox-4.0
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get install firefox

```

These will purge your unstable Firefox 4 installation and install the stable Firefox 4 version from mozillateam firefox-stable ppa.

Keep in mind that thew repository you was using probably cloned your Firefox profile folder **~/.mozilla/firefox** to **~/.mozilla/firefox-4.0**. So if you miss something like recent saved bookmarks or passwords, you might need to import them them from the cloned profile.

I don't have the software sources option in my menu from administration (I am am the only user on this so I should be able to see every feature)

---

### Post by jiggajoe506 on 2011-04-19
> **ClientAlive said:**
> * _jiggajoe_ - Are you using a Macintosh machine? I noticed the apple icon on the corner of the window in one of your pictures. Not sure how much of a difference that observation makes but I thought I should share it.

Thanks
Jake

haha any input is good in put to me brother thanks but it just came with the theme i got and haven't changed it to **** off my mac friend about how much better ubuntu is :)

---

### Post by alphacrucis2 on 2011-04-19
> **jiggajoe506 said:**
> I don't have the software sources option in my menu from administration (I am am the only user on this so I should be able to see every feature)

Go to system - preferences - main menu

Scroll down the left hand pane and select System - Administration. You will see that only the items ticked on the right hand pane will display in the menu. You should find Software Sources unticked. Click the checkbox and that should make it display on the gnome menu. You can also get into Software Sources via a menu item within Synaptic Package Manager

---

### Post by jiggajoe506 on 2011-04-19
Guys thanks for holding my hand and helping me get through this. I tried to do an update and this is what I came up with... sorry I am such an ouf ha

---

### Post by alphacrucis2 on 2011-04-19
> **jiggajoe506 said:**
> Guys thanks for holding my hand and helping me get through this. I tried to do an update and this is what I came up with... sorry I am such an ouf ha

Looks like you haven't got the authentication key installed for the moz ppa. You can copy the key from launchpad and save it in a file to import in Software Sources. Normally the command posted by Loving Linux should have import the authkey:

```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```

---

### Post by jiggajoe506 on 2011-04-19
> **alphacrucis2 said:**
> Looks like you haven't got the authentication key installed for the moz ppa. You can copy the key from launchpad and save it in a file to import in Software Sources. Normally the command posted by Loving Linux should have import the authkey:

```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```

I am slowly getting the grip of this... kinda glad that you guys are so helpful and patient with me, kinda glad this is happening b/c I have learned more in one day then I have for the 4 months that I've had this. Can you explain the process to me? Thanks in advance.

---

### Post by jiggajoe506 on 2011-04-19
Tried running it but came up with the following

---

### Post by alphacrucis2 on 2011-04-19
> **jiggajoe506 said:**
> Tried running it but came up with the following


For some reason it is getting a timeout trying to download the authkey from the key server. Possibly the keyserver is down at the mo. You can do it manually instead.

Step 1. Go to the moz firefox stable ppa web page:

[URL="https://launchpad.net/~mozillateam/+archive/firefox-stable"]https://launchpad.net/~mozillateam/+archive/firefox-stable
[/URL]

Step 2. Click the link that says "Technical Details about this PPA". The will then display some more info. Click the link immediately below where it says "Signing Key: That should give a search result listing one line starting "pub 1024R". Click the first link on that line. It will display the encoded signing key which will be a whole lot of gobbledegook.

Step 3. Drag over the signing key text using your mouse including the line at the beginning and end so all the text is highlighted

 -----BEGIN PGP PUBLIC KEY BLOCK-----
blah blah gobbledegook several lines
-----END PGP PUBLIC KEY BLOCK-----

Do a Edit Copy or CTRL c as you prefer.

Step 4. Start up Applications - Accessories - Text Editor and paste the text you copied in step 3.

Step 5. In the text editor. Save As (make up a file name say mozstablekey) under Desktop or a folder of your choice. Close the Text Editor.

Step 6. Run Software Sources like you did before. Select Authentication and Click import key file. Point it at the file you saved in Step 5.

Done. Rerun Lovinglinux's commands.

---

### Post by jiggajoe506 on 2011-04-21
hey guys thanks for all the help with mozilla, it is working fine now. Sorry I went M.I.A yesterday I had a full day of finals. Of course I have another problem... Everytime i try to update now there is this message.

Is there a way to get a key for all of my progams i currently have installed?

---

### Post by ClientAlive on 2011-04-23
> **jiggajoe506 said:**
> haha any input is good in put to me brother thanks but it just came with the theme i got and haven't changed it to **** off my mac friend about how much better ubuntu is :)

Oh, just to clarify - I just thought the information might be useful for what you're trying to do here.

Congrats on getting Firefox working.

Now, here's something to really put you're noodle in a twist!

[http://www.youtube.com/watch?v=sMaViXG0KWw](http://www.youtube.com/watch?v=sMaViXG0KWw)

[http://www.youtube.com/watch?v=6HI1zvWHPuE](http://www.youtube.com/watch?v=6HI1zvWHPuE)

That's the one I'm running and I love it! Fast as frickin' lightning!

Here's a benchmark test a guy did comparing it with 5 others (including Firefox).

[http://www.youtube.com/watch?v=suYwbbQCN6A](http://www.youtube.com/watch?v=suYwbbQCN6A)

I can be so evil sometimes . . . lollllllllllll
:roll:


Be blessed brother. Welcome to Ubuntu Linux!

----------------------------------

PS: If the issue has been solved you can "mark this thread as solved" in the drop down menu under "Thread Tools" near the top of the page.

---

### Post by alphacrucis2 on 2011-04-23
> **jiggajoe506 said:**
> hey guys thanks for all the help with mozilla, it is working fine now. Sorry I went M.I.A yesterday I had a full day of finals. Of course I have another problem... Everytime i try to update now there is this message.

Is there a way to get a key for all of my progams i currently have installed?

The key isn't for a specific program, it's for the whole ppa. Have a look at your software sources, maybe you enabled the moz daily ppa as well as the stable. Just disable the daily one unless you want to be on the bleeding edge. Or else install its' signing key as per above. You don't normally have to do that as apt-add-repository should pull the signing key from the key server. It looked like the keyserver may have been down so it timed out on you when you ran the apt-add-repository command. If a ppa ever causes you a problem you can back them out using a program called ppapurge. It's a useful tool to install if you are using ppa's.

---

