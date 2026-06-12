---
title: "How do I install Google Earth in 10.10?"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by TopFan on 2010-10-13
Title says it all. I've tried numerous methods that have worked on past versions of Ubuntu, but none of them seem to work now.

---

### Post by alphacrucis2 on 2010-10-13
> **TopFan said:**
> Title says it all. I've tried numerous methods that have worked on past versions of Ubuntu, but none of them seem to work now.

Medibuntu don't have it for Maverick yet.

Have you tried:

```
sudo apt-get install googlearth-package
make-googleearth-package --force
sudo dpkg -i *.deb
```

If you are running 64 bit you also have to make sure that the ia32-libs package is installed. I would be interested to know how you get on as for me it just crashes with a signal 6 error on startup just after displaying the googleearth splash screen.

---

### Post by oldos2er on 2010-10-13
Download GoogleEarthLinux.bin ([http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html)), open a terminal and run ```
cd Downloads
chmod a+x GoogleEarthLinux.bin
sudo ./GoogleEarthLinux.bin
```

---

### Post by oldos2er on 2010-10-13
[delete]

---

### Post by TopFan on 2010-10-13
I've cut and pasted both suggested codes into Terminal, but no luck.

After pasting Ann's code, terminal asks me for my password, but won't let me type anything.

---

### Post by emoguitarist06 on 2010-10-13
Check this site ;)
[http://www.omgubuntu.co.uk/2010/10/google-earth-plays-nice-with-compiz-and-ubuntu-10-10/]("http://www.omgubuntu.co.uk/2010/10/google-earth-plays-nice-with-compiz-and-ubuntu-10-10/")

---

### Post by natravis on 2010-10-13
> **TopFan said:**
> I've cut and pasted both suggested codes into Terminal, but no luck.

After pasting Ann's code, terminal asks me for my password, but won't let me type anything.

It will appear that you aren't typing anything, but if you type in your password then hit enter, stuff will happen. Magic!

---

### Post by TopFan on 2010-10-13
> **natravis said:**
> It will appear that you aren't typing anything, but if you type in your password then hit enter, stuff will happen. Magic!

I tried that, but it didn't work.

Here's what I get when I paste Ann's code into terminal:

topfan@topfanlaptop:~$ cd Downloads
topfan@topfanlaptop:~/Downloads$ chmod a+x GoogleEarthLinux.bin
chmod: cannot access `GoogleEarthLinux.bin': No such file or directory
topfan@topfanlaptop:~/Downloads$ sudo ./GoogleEarthLinux.bin

It no longer asks me for my password. GoogleEarthLinux.bin is on my desktop, but terminal can't see it.

---

### Post by redbook4574 on 2010-10-13
> **TopFan said:**
> I tried that, but it didn't work.

Here's what I get when I paste Ann's code into terminal:

topfan@topfanlaptop:~$ cd Downloads
topfan@topfanlaptop:~/Downloads$ chmod a+x GoogleEarthLinux.bin
chmod: cannot access `GoogleEarthLinux.bin': No such file or directory
topfan@topfanlaptop:~/Downloads$ sudo ./GoogleEarthLinux.bin

It no longer asks me for my password. GoogleEarthLinux.bin is on my desktop, but terminal can't see it.

Ok here goes, slightly convoluted but it worked for me.

1. install googleearth-package in synaptic
2. open a terminal window and run "sudo make-googleearth-package --force" (without the quotation marks).

3. This will take approx 10 mins to complete and will generate many errors, don't worry about these just now.

4. When step 3 has completed run the following command in terminal "sudo dpkg -i googleearth_5.2.1.1588+0.5.7-1_i386.deb"

5. All being well you should now have google earth in application-internet.

6. If it crashes on opening, in terminal run "gedit ~/.config/Google/GoogleEarthPlus.conf" and if the line enableTips=true exists change it to enableTips=false, if it does not exist add the line enableTips=false under the[General] heading and save the file.

Hopefully everything will then work.

---

### Post by oldos2er on 2010-10-13
> **TopFan said:**
> I tried that, but it didn't work.

Here's what I get when I paste Ann's code into terminal:

topfan@topfanlaptop:~$ cd Downloads
topfan@topfanlaptop:~/Downloads$ chmod a+x GoogleEarthLinux.bin
chmod: cannot access `GoogleEarthLinux.bin': No such file or directory
topfan@topfanlaptop:~/Downloads$ sudo ./GoogleEarthLinux.bin

It no longer asks me for my password. GoogleEarthLinux.bin is on my desktop, but terminal can't see it.

I thought you would download it to your ~/Downloads directory; if it's on your desktop, run **cd Desktop** instead.

---

### Post by empty_spaces on 2010-10-13
> **TopFan said:**
> I tried that, but it didn't work.

Here's what I get when I paste Ann's code into terminal:

topfan@topfanlaptop:~$ cd Downloads
topfan@topfanlaptop:~/Downloads$ chmod a+x GoogleEarthLinux.bin
chmod: cannot access `GoogleEarthLinux.bin': No such file or directory
topfan@topfanlaptop:~/Downloads$ sudo ./GoogleEarthLinux.bin

It no longer asks me for my password. GoogleEarthLinux.bin is on my desktop, but terminal can't see it.

Why are you doing a "cd Downloads" when you have GoogleEarthLinux.bin on your desktop?

---

### Post by HobbitTR on 2010-10-14
> **redbook4574 said:**
> 
1. install googleearth-package in synaptic
2. open a terminal window and run "sudo make-googleearth-package --force" (without the quotation marks).

3. This will take approx 10 mins to complete and will generate many errors, don't worry about these just now.

4. When step 3 has completed run the following command in terminal "sudo dpkg -i googleearth_5.2.1.1588+0.5.7-1_i386.deb"

5. All being well you should now have google earth in application-internet.

6. If it crashes on opening, in terminal run "gedit ~/.config/Google/GoogleEarthPlus.conf" and if the line enableTips=true exists change it to enableTips=false, if it does not exist add the line enableTips=false under the[General] heading and save the file.


I am using a Dell Inspiron 1520 with NVidia driver ver: 173.14.28
redbook's install steps worked GREAT for me :)

1) I used aptitude instead of synaptic.
2) I set the startup command to /usr/bin/googleearth because I got the following error from the default GoogleEarth command of:
googleearth %f
"Couldn't run Google Earth (googleearth-bin). Is GOOGLEEARTH_DATA_PATH set?"
3) When I used /usr/bin/googleearth it still crashed.
4) When I changed the enableTips to false it ran fine. 
Thank you!

---

### Post by Dave&quot;B&quot; on 2010-10-14
Hi Anne,
I tried your advice - alas, it gives me an error ( pasted below). I am brand new to UBUNTU, installed only last night.

[B][I]david@david-Latitude-D620:~/Downloads$ chmod a+x GoogleEarthLinux.bin
david@david-Latitude-D620:~/Downloads$ sudo ./GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.2.1.1588..............................................................
setup.data/setup.xml:1: parser error : Document is empty

^[/I][I]
setup.data/setup.xml:1: parser error : Start tag expected, '<' not found

^[/I][I]
Couldn't load 'setup.data/setup.xml'[/I][/B]

---

### Post by avanhel on 2010-10-14
I use an easier method.
Have a look at the Medibuntu entry in the community documentation
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

After you have added the medibuntu repository, you can just add Google earth using the ubuntu software centre.

---

### Post by oldos2er on 2010-10-14
As was noted in post #2, Medibuntu doesn't have google-earth for 10.10.

---

### Post by gandaran on 2010-10-14
> **Dave"B" said:**
> Hi Anne,
I tried your advice - alas, it gives me an error ( pasted below). I am brand new to UBUNTU, installed only last night.

[B][I]david@david-Latitude-D620:~/Downloads$ chmod a+x GoogleEarthLinux.bin
david@david-Latitude-D620:~/Downloads$ sudo ./GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.2.1.1588..............................................................
setup.data/setup.xml:1: parser error : Document is empty

^[/I][I]
setup.data/setup.xml:1: parser error : Start tag expected, '<' not found

^[/I][I]
Couldn't load 'setup.data/setup.xml'[/I][/B]
probably the download is corrupted! download the .bin file again.
if you still have any problem installing the .bin file then try the other (only ubuntu 10.10) method
```
sudo apt-get install googlearth-package
make-googleearth-package --force
```
run the commands in terminal, the first one installs the google earth build utility and the second downloads the .bin package to the user directory and builds the .deb package out of it which you can install with ubuntu software center and also remove it the same way.

---

### Post by TopFan on 2010-10-14
Hi Ann (and everyone).

Thank you for your help - I appreciate it.

> **oldos2er said:**
> I thought you would download it to your ~/Downloads directory; if it's on your desktop, run **cd Desktop** instead.

I've tried this with 'Desktop' and got the following:

topfan@topfanlaptop:~$ cd Desktop
topfan@topfanlaptop:~/Desktop$ chmod a+x GoogleEarthLinux.bin
topfan@topfanlaptop:~/Desktop$ sudo ./GoogleEarthLinux.bin
[sudo] password for topfan:
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.2.1.1588..............................................................
setup.data/setup.xml:1: parser error : Document is empty

^
setup.data/setup.xml:1: parser error : Start tag expected, '<' not found

^
Couldn't load 'setup.data/setup.xml'
topfan@topfanlaptop:~/Desktop$

Is it possible that Google Earth is not yet compatible with 10.10? Out of interest, does anyone know why GE is not available from the Software Centre - it is such a great piece of software!

---

### Post by TopFan on 2010-10-14
Wow! I didn't see all the responses on pg 2 - I bookmarked this topic (i.e. page 1) yesterday and didn't spot pg 2 until after my last post. Schoolboy error - sorry! I'll review pg 2 tonight.

> **empty_spaces said:**
> Why are you doing a "cd Downloads" when you have GoogleEarthLinux.bin on your desktop?

Because that's the code I was given! Being an 'Absolute Beginner' [the clue's in the forum title :P ] I haven't got a clue about 'Terminal'. Terminal is an out of date way of interacting with a computer. Everything should be done via menus of GUI. Until it's done that way in Ubuntu, this great OS will remain on the sidelines. But thanks for your contribution. :P

---

### Post by oldos2er on 2010-10-14
For the parser error, try [http://ca.ubuntuforums.org/showthread.php?p=9923137](http://ca.ubuntuforums.org/showthread.php?p=9923137)

"Terminal is an out of date way of interacting with a computer."

That's one opinion. :) I would've said it's a fundamental way of interacting with a computer, particularly a Linux machine.

Post back if you need more help.

---

### Post by alliance1975 on 2010-10-15
Tried all the suggestions and nothing works. Is there anyone out there that actually got GE to work in 10.10?

---

### Post by k3lt01 on 2010-10-15
Go to [this page]("http://packages.medibuntu.org/lucid/googleearth.html"), scroll down to the bottom and download the version you need (amd64 or i386). Save it to your desktop. Right clock on it and select open with Ubuntu Software Centre. It will then install IF everything else you have done so far doesn't block it from doing so. If it is stopped from installing you will need to clean up the attempted installs you have done before this.

---

### Post by beew on 2010-10-16
I am not sure why you must have google earth right the way. If you are having problems installing manually then just wait for it to appear in Medibuntu. Another option would be to install the package worldwind from Synaptic, it is similar to but probably better google earth (google "WorldWind" or "NASA Worldwind", I wanted to provide a link but it seems that the server is down at the moment)

---

### Post by beew on 2010-10-16
> **k3lt01 said:**
> Go to [this page]("http://packages.medibuntu.org/lucid/googleearth.html"), scroll down to the bottom and download the version you need (amd64 or i386). Save it to your desktop. Right clock on it and select open with Ubuntu Software Centre. It will then install IF everything else you have done so far doesn't block it from doing so. If it is stopped from installing you will need to clean up the attempted installs you have done before this.

I hate to install .deb files with the SC, it just seems unnecessarily elaborate. gdebi should be the default way to install .deb packages like it is in Lucid(and before?), but for some reasons it is not even installed anymore by default and you have to install it via Synaptic (or the SC, which I never use)

---

### Post by k3lt01 on 2010-10-16
> **beew said:**
> I hate to install .deb files with the SC, it just seems unnecessarily elaborate. gdebi should be the default way to install .deb packages like it is in Lucid(and before?), but for some reasons it is not even installed anymore by default and you have to install it via Synaptic (or the SC, which I never use)If you think this then post in the Natty forum and suggest it. Better still post your request in Launchpad.

The fact of the matter is the OP asked how to do it in 10.10. I have given the appropriate advice for the OP to succeed IF they haven't caused further complications by using the GE bin file.

---

### Post by alphacrucis2 on 2010-10-16
> **beew said:**
> I hate to install .deb files with the SC, it just seems unnecessarily elaborate. gdebi should be the default way to install .deb packages like it is in Lucid(and before?), but for some reasons it is not even installed anymore by default and you have to install it via Synaptic (or the SC, which I never use)

Just install gdebi and make it the default program for deb files in Nautilus. 

BTW. I had success with googleearth in 10.10. I had to reinstall the ia32-libs. Removing it took out skype, picasa and a couple of other 32 bit apps. After reinstalling ia32-libs, I installed the Lucid 64 googleearth package from Medibuntu and reinstalled the other apps that were removed and everything is now working ok. The medibuntu version is 5.1 rather than 5.2 but at least it works. I will have another go at 5.2 later in the week when I have time.
 
It's possible I had a funny version of the ia32-libs from a PPA when I was running Lucid that may have been the cause of my trouble.

---

### Post by beew on 2010-10-16
> **k3lt01 said:**
> If you think this then post in the Natty forum and suggest it. Better still post your request in Launchpad.

The fact of the matter is the OP asked how to do it in 10.10. I have given the appropriate advice for the OP to succeed IF they haven't caused further complications by using the GE bin file.

I did not say your advice was inappropriate. Why get so defensive?

---

### Post by k3lt01 on 2010-10-16
> **beew said:**
> I did not say your advice was inappropriate. Why get so defensive?That post wasn't defensive. I was giving you some advice and re-enforcing my previous post for the OP so they didn't think they had to go and install gdebi.

---

### Post by TopFan on 2010-10-17
> **k3lt01 said:**
> Go to [this page]("http://packages.medibuntu.org/lucid/googleearth.html"), scroll down to the bottom and download the version you need (amd64 or i386...

Yipee! Thanks for this. It's an old version of GE, so not perfect, but it'll do.

Thank you all for your contributions and help.

---

### Post by oldos2er on 2010-10-17
> **alliance1975 said:**
> Tried all the suggestions and nothing works. Is there anyone out there that actually got GE to work in 10.10?

Yes, v5.2.1.1588 works fine here.

---

### Post by lindsay7 on 2010-10-18
> **redbook4574 said:**
> Ok here goes, slightly convoluted but it worked for me.

1. install googleearth-package in synaptic
2. open a terminal window and run "sudo make-googleearth-package --force" (without the quotation marks).

3. This will take approx 10 mins to complete and will generate many errors, don't worry about these just now.

4. When step 3 has completed run the following command in terminal "sudo dpkg -i googleearth_5.2.1.1588+0.5.7-1_i386.deb"

5. All being well you should now have google earth in application-internet.

6. If it crashes on opening, in terminal run "gedit ~/.config/Google/GoogleEarthPlus.conf" and if the line enableTips=true exists change it to enableTips=false, if it does not exist add the line enableTips=false under the[General] heading and save the file.

Hopefully everything will then work.

This work great for me, just had to change to ..amd64.deb for my system

---

### Post by ma3cs on 2010-10-18
[http://packages.medibuntu.org/pool/non-free/g/googleearth/](http://packages.medibuntu.org/pool/non-free/g/googleearth/)

install from here .. just click

---

### Post by GiovanniEmex on 2010-10-18
> **k3lt01 said:**
> Go to [this page]("http://packages.medibuntu.org/lucid/googleearth.html"), scroll down to the bottom and download the version you need (amd64 or i386). Save it to your desktop. Right clock on it and select open with Ubuntu Software Centre. It will then install IF everything else you have done so far doesn't block it from doing so. If it is stopped from installing you will need to clean up the attempted installs you have done before this.

I installed from the lucid repository, it installed quite easy, but every time I open it says it cannot connect to the server "http://kh.google.com:80/". In the Google site says that I must make an exception in the firewall... but as far as I know it is not activated. The gufw doesn't have a lot of help, either.

How can I make the application to work?

---

### Post by k3lt01 on 2010-10-19
Sorry Giovanni I don't know the answer to your question as I haven't come across that problem. I hope someone else is able to help.

---

### Post by k3lt01 on 2010-10-19
> **ma3cs said:**
> [http://packages.medibuntu.org/pool/non-free/g/googleearth/](http://packages.medibuntu.org/pool/non-free/g/googleearth/)

install from here .. just clickHere's a question for you, what one does a noob who doesn't know much about Ubuntu .. just click? I gave 1 link with 2 files (1 i386 and the other amd64 both of which are .deb files) so the person has 2 choices. The link you gave has 132 choices 10 of which are .deb files. Which one of 132 (or 10 if they know about .debs files) do they choose?

---

### Post by ma3cs on 2010-10-19
googleearth_5.1.3533.1731-0medibuntu1_i386.deb	23-Jan-2010 19:09 	 17M

Work for me ! 

PS. Many files from there are changelog or copyright.

---

### Post by oldos2er on 2010-10-19
> **k3lt01 said:**
>  Which one of 132 (or 10 if they know about .debs files) do they choose?

The most recent version. If they are unsure they can always ask here in the forums.

---

### Post by k3lt01 on 2010-10-19
> **ma3cs said:**
> googleearth_5.1.3533.1731-0medibuntu1_i386.deb	23-Jan-2010 19:09 	 17M

Work for me ! 

PS. Many files from there are changelog or copyright.I know what the files are, I'm not a noob anymore even though I don't know everything there is to know. I was trying to get you to be a little bit clearer for our noob friends who wouldn't have the foggiest idea what they are doing and that is often the reason they are here asking for help.

P.S. If you took a look at the link I gave that file is on that page. Talk about going the long way to do something ](*,)

---

### Post by ma3cs on 2010-10-19
must be love if you insist so much ....

:guitar:

---

### Post by k3lt01 on 2010-10-19
To TopFan Don't forget to mark this thread as Solved so others can see it works without having to start a new thread.

> **ma3cs said:**
> must be love if you insist so much ....

:guitar:What?

---

### Post by alphacrucis2 on 2010-10-19
While Medibuntu's 5.1 package for Lucid 64 bit is now working for me in Maverick 64 bit, I'm still trying to get 5.2 to work. For me 5.2 crashes with Signal 11 shortly after the main window appears. I am following up with some ideas I read on the google support forums which I will try out later today and report back.

---

### Post by TopFan on 2010-10-20
> **k3lt01 said:**
> To TopFan Don't forget to mark this thread as Solved so others can see it works without having to start a new thread.
 Good idea. How do I do that though? Can't see an obvious way.

---

### Post by k3lt01 on 2010-10-20
Go to the "Thread Tools" drop down menu at the top of the page and select Solved there.

---

### Post by TopFan on 2010-10-20
Ta!

---

### Post by bedlam on 2010-10-23
Very helpful. I've just used your convoluted approach to install earth in 10.10
and it worked fine after it crashed and I added the line "Tips=false"

---

### Post by marwansherin on 2010-11-10
hi, i was have too this error you only need do this
in terminal like root write this  

./GoogleEarthLinux.bin --target /tmp/ge
cd /tmp/ge/setup.data/bin/Linux/x86/
mv setup.gtk setup.gtk2
cd /tmp/ge
./setup.sh

Good Luck,

---

### Post by grapperman on 2010-11-12
> **marwansherin said:**
> hi, i was have too this error you only need do this
in terminal like root write this  

./GoogleEarthLinux.bin --target /tmp/ge
cd /tmp/ge/setup.data/bin/Linux/x86/
mv setup.gtk setup.gtk2
cd /tmp/ge
./setup.sh

Good Luck,
Many thanks. Worked a treat!

---

### Post by L Campbell on 2010-11-12
> **k3lt01 said:**
> Go to [this page]("http://packages.medibuntu.org/lucid/googleearth.html"), scroll down to the bottom and download the version you need (amd64 or i386). Save it to your desktop. Right clock on it and select open with Ubuntu Software Centre. It will then install IF everything else you have done so far doesn't block it from doing so. If it is stopped from installing you will need to clean up the attempted installs you have done before this.

Thanks for your suggestion here.

It worked like a trump card for me.

---

### Post by ulnsterile on 2010-11-13
hey redbook4574 thanKs a million!!!...it worked for me...WOW

---

### Post by ulnsterile on 2010-11-13
1. install googleearth-package in synaptic
2. open a terminal window and run "sudo make-googleearth-package --force" (without the quotation marks).

3. This will take approx 10 mins to complete and will generate many errors, don't worry about these just now.

4. When step 3 has completed run the following command in terminal "sudo dpkg -i googleearth_5.2.1.1588+0.5.7-1_i386.deb"

5. All being well you should now have google earth in application-internet.

yeah this one worked for me...hey redbook4574 thanKs a million!!!...it worked for me...WOW

---

### Post by wkhasintha on 2010-11-13
Goody. I wanted to install GEarth too. awesome thread,

---

### Post by rmf1975 on 2010-11-14
> **k3lt01 said:**
> Go to [this page]("http://packages.medibuntu.org/lucid/googleearth.html"), scroll down to the bottom and download the version you need (amd64 or i386). Save it to your desktop. Right clock on it and select open with Ubuntu Software Centre. It will then install IF everything else you have done so far doesn't block it from doing so. If it is stopped from installing you will need to clean up the attempted installs you have done before this.


[SIZE=5][COLOR=Green]Thanks alot, Mr.k3lt01:)[/COLOR][/SIZE]

---

