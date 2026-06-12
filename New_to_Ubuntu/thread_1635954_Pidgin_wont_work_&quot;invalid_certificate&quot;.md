---
title: "Pidgin wont work &quot;invalid certificate&quot;"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by spoonlol on 2010-12-02
hi 
everytime i try to sign in using pidgen i get this error:
The certificate chain presented by omega.contacts.msn.com does not have a valid digital signature from the Certificate Authority from which it claims to have a signature.
any ideas?

---

### Post by squaregoldfish on 2010-12-02
I think an update was released yesterday with a workaround to this.
Steve.

---

### Post by spoonlol on 2010-12-02
how would i apply this update to the aplication?

---

### Post by squaregoldfish on 2010-12-03
The update should be available through Ubuntu's update manager tool.

---

### Post by amjjawad on 2010-12-03
If you have that application installed, then the update should be applied automatically.
I saw that update and I just updated my system this morning. However, I removed Pidgin because that error was a real pain.

Please, if that update fixed the issue, let us know.

Thank you :)

---

### Post by squaregoldfish on 2010-12-04
I can confirm that the update fixes the issue.
Steve.

---

### Post by amjjawad on 2010-12-04
> **squaregoldfish said:**
> I can confirm that the update fixes the issue.
Steve.

Thanks Steve. Will install it again and see what will happen :)

---

### Post by amjjawad on 2010-12-04
I installed Pidgin again. Still didn't try it yet.
Was just wondering if I need to install more than:

[B][I]Pidgin
Pidgin-libnotify[/I][/B]

When I mark Pidgin for installation, it picks two files (above) and that's all. Is there any other thing I need to do? just wondering. Yeah, I know about plug-ins but I mean something else which is necessary. However, I guess Synaptic picks everything related already.

Thank you!

---

### Post by uRock on 2010-12-04
I ubuntu on a thumb drive that can't be updated, so uninstalled pidgin, then reinstalled it so that it would grab the newest version and it did. The MSN certificate problem went away.

As for my full installs, the update a few days ago foxed the problem.

The two packages listed above are all pidgin needs.

---

### Post by karthick87 on 2010-12-04
Update your pidgin to the latest version,

To add repository type the following in terminal,

```
sudo add-apt-repository ppa:pidgin-developers/ppa
```

Update your repository,

```
sudo apt-get update
```

Install Pidgin,

```
sudo apt-get install pidgin
```

This will update your existing pidgin to the latest release **2.7.7**

---

### Post by amjjawad on 2010-12-04
> **karthick87 said:**
> Update your pidgin to the latest version,

To add repository type the following in terminal,

```
sudo add-apt-repository ppa:pidgin-developers/ppa
```Update your repository,

```
sudo apt-get update
```Install Pidgin,

```
sudo apt-get install pidgin
```This will update your existing pidgin to the latest release **2.7.7**

Thanks a lot, Synaptic is updated now. However, when Pidgin is running and I check the version from Help > About ... it says 2.6.6.

Whenever I remove it completely, it seems that many files are still there. Whenever I re-install it, I don't need to configure my account(s) because everything is there which means the data is there. I know in Ubuntu we can't remove everything and we have to do it manually sometimes/most of the times.

Is there anyway to get the latest Pidgin installed and un-install the old one permanently,?

---

### Post by karthick87 on 2010-12-04
No need of removing the old one.The install will update the existing version to the new one.Just it requires a reboot to show the updated version.

---

### Post by amjjawad on 2010-12-04
> **karthick87 said:**
> No need of removing the old one.The install will update the existing version to the new one.**Just it requires a reboot** to show the updated version.

Done.
Thank you so much :)

I hope the OP will read this and follow these steps.

---

### Post by davesmith on 2010-12-05
I'm using 8.04 Hardy Heron on an old Tosh Satellite A30 laptop. My pidgin won't update and I've got this certificate problem on pidgin 2.7.0. It connects to MSN and I can see my buddies but it will not work with ICQ or AIM. "invalid requested host"

There is something dodgy about IM apps these days. My m8 Ratspeaker looked into this last night using OTR and continually got a message "man-in-the-middle attack" and "Re-boot & re-connect - security risk of third party interception"

What is going on here? I thought using Ubuntu avoided security problems. Can anyone explain?

---

### Post by amjjawad on 2010-12-05
> **davesmith said:**
> What is going on here? I thought using Ubuntu avoided security problems. Can anyone explain?

Using Ubuntu or whatever Operating System will not prevent such errors. After all, these applications aren't made for Ubuntu ONLY nor these are native Ubuntu's Apps.
Not sure how to explain that in words but such issues could happen in any System. Keep in mind, there's NO perfect OS.

Just wanted to share my opinion :)

---

### Post by karthick87 on 2010-12-05
> **davesmith said:**
> I'm using 8.04 Hardy Heron on an old Tosh Satellite A30 laptop. My pidgin won't update and I've got this certificate problem on pidgin 2.7.0. It connects to MSN and I can see my buddies but it will not work with ICQ or AIM. "invalid requested host"

There is something dodgy about IM apps these days. My m8 Ratspeaker looked into this last night using OTR and continually got a message "man-in-the-middle attack" and "Re-boot & re-connect - security risk of third party interception"

What is going on here? I thought using Ubuntu avoided security problems. Can anyone explain?

Did you get any errors during update?

---

### Post by davesmith on 2010-12-05
I used the terminal to do the update

<sudo aptitude update>

then <sudo aptitude safe-upgrade>

there was no update for pidgin or libpurple

so I tried <sudo apt-get install pidgin>

and the reply was  "the latest version is already installed"

so i'm stuck now!

---

### Post by karthick87 on 2010-12-05
What version you are using currently?

```
pidgin -v
```

---

### Post by davesmith on 2010-12-05
pidgin 2.7.0

Today MSN works and I can see my buddies, but ICQ and AIM give the error

"Received unexpected response from [https://api.oscar.aol.com/aim/startOSCARSession:](https://api.oscar.aol.com/aim/startOSCARSession:) Invalid requested host"

And pidgin still will not update to 2.7.7

---

### Post by karthick87 on 2010-12-05
Have you added the repository??

---

### Post by bug67 on 2010-12-05
I've been watching this thread from afar.  I too was having this problem until the new Pidgin update.  If, however you are for some reason not able to install the update, this is what had worked for me in the interim:

[http://www.webupd8.org/2010/11/fix-pidgin-msn-omegacontactsmsncom.html](http://www.webupd8.org/2010/11/fix-pidgin-msn-omegacontactsmsncom.html)

---

### Post by davesmith on 2010-12-05
I am on 8.04 hardy heron. using the terminal unfortunately it does not recognise "add-apt-repository" as a command. How do I as the repository using hardy?

---

### Post by davesmith on 2010-12-05
Unfortunately in pidgin 2.7.0 there is no "Tools" menu - but i managed to install the certificate manually, it fixed the MSN problem.

The issue is icq and aim will not work!

---

### Post by IndyGunFreak on 2010-12-05
It should work just fine for Hardy as well.. If that doesn't work though... try this.

Go here.  [http://pidgin.im/download/ubuntu/](http://pidgin.im/download/ubuntu/)
Download the .deb file, and double click to "install" it.  That will add Pidgin's PPA repository.

Then in a terminal, 
sudo apt-get update
sudo apt-get upgrade

When you run the upgrade, you should see the new pidgin packages available.

---

### Post by karthick87 on 2010-12-05
You have edit sources.list Goto terminal and type the following
```
sudo gedit /etc/apt/sources.list
```This will open a text editor containing the list of archives that your system is currently using.Scroll to the bottom of the file and paste the following two lines there.

**For Hardy**
```
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu hardy main 
deb-src http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu hardy main 
```[B]For Karmic
[/B]```
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu karmic main 
deb-src http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu karmic main
```**For Lucid**
```
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu lucid main 
deb-src http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu lucid main 
```**For Maverick**
```
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu maverick main 
deb-src http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu maverick main 
```Save the file and exit the text editor.Now you should add the key to your system,in terminal type the following
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A1F196A8
```Now from terminal update your repositories.
```
sudo apt-get update 
```Install pidgin,
```
sudo apt-get install pidgin
```

---

### Post by davesmith on 2010-12-05
Thanks for your help

I added the lucid to the repositories on my hardy heron system as described
<deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) lucid main>

when I run <sudo apt-get update> in the terminal I get the error:-

"W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7FB8BEE0A1F196A8"

Well.....it looked ike it should work, but it did'nt!

---

### Post by uRock on 2010-12-05
You can get the key here [https://launchpad.net/~pidgin-developers/+archive/ppa/](https://launchpad.net/~pidgin-developers/+archive/ppa/)

---

### Post by davesmith on 2010-12-05
Thank you. I have copied the key from the pidgin developer's website. Could you tell me where to put it, and what happens next?

---

### Post by karthick87 on 2010-12-05
Now you should add that key to your system,in terminal type the following

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A1F196A8
```

Now from terminal update your repositories.

```
sudo apt-get update
```

Install pidgin,

```
sudo apt-get install pidgin
```

---

### Post by uRock on 2010-12-05
Thanks for posting that Karthick. I was just getting ready to post the same thing. 

Dave, If you already have an older version of Pidgin installed, then after you run the key command you just need to run **sudo apt-get update && sudo apt-get upgrade** to get the latest version.

---

### Post by Penguin=) on 2010-12-05
Re-install ALL of the Pidgin components, see if it works, oh yeah i almost forgot, make sure you restart your computer after doing this!

---

### Post by davesmith on 2010-12-05
Ah, thank you. I have followed the instructions carefully from the ppa site - which are the same as yours. The certificate is installed. 

However, the next step, using 
<sudo apt-get install pidgin>
the terminal responded
"pidgin is already the newest version."
which is back where i started, pidgin 2.7.0, and not 2.7.7 as i had hoped

---

### Post by karthick87 on 2010-12-05
Have you updated the repositories??

---

### Post by davesmith on 2010-12-05
Thank you Karthic and uRock for your help - i have updated the repositories as described, found and installed the 8.04 key but no upgrade.

I also re-installed pidgin and pidgin data using synaptic but it is still the same version - 2.7.0

I may need a cup of tea here, to fortify myself for what may turn into a long evening. This problem has intrigued me now and i am determined to fix it. Can I check that version 2.7.7 is actually available for hardy?

---

### Post by uRock on 2010-12-05
> **Penguin=) said:**
> Re-install ALL of the Pidgin components, see if it works, oh yeah i almost forgot, make sure you restart your computer after doing this!
Lol, what? This isn't Windows.;)

You do have to restart Pidgin for the update to take effect, but that can be done with **killall pidgin** in the terminal.

> **davesmith said:**
> Can I check that version 2.7.7 is actually available for hardy?
According to the Pidgin site, their repos only update for 10.04 and newer. [http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)

---

### Post by uRock on 2010-12-05
If you really want 2.7.7, then you can download the tar.gz2 package from their site. [http://www.pidgin.im/download/source/](http://www.pidgin.im/download/source/)

---

### Post by davesmith on 2010-12-05
uRock, what really I want is for pidgin to work and connect to my MSN, ICQ and AIM a/c's. The consensus on this forum seemed to be that pidgin 2.7.7 solved the certificate problem reported as an error when i try and start pidgin

"The certificate for omega.contacts.msn.com could not be validated. The certificate chain presented is invalid."

I am repared to try the tar.gz file. Do you just click on it after it's downloaded, or is there some code i can use in the terminal? I always d/l files to the desktop.

---

### Post by uRock on 2010-12-05
When I updated to 2.6.6 the issue was fixed for me. I only added the PPA to help have the problem fixed faster in the future when MSN decides to make changes to their protocols.

Once the tarball is downloaded to the /home folder you can follow the directions on this link [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) I have never done an install this way, so I can't be of much direct help.

---

### Post by amjjawad on 2010-12-05
Did anyone notice that the OP didn't show up yet? :D

I hope all these info will be helpful for him and everyone else. I'm enjoying reading this thread :)

---

### Post by uRock on 2010-12-05
> **amjjawad said:**
> Did anyone notice that the OP didn't show up yet? :D

I hope all these info will be helpful for him and everyone else. I'm enjoying reading this thread :)

Just running updates should have fixed his/her problem. Hopefully the lack of response means that it did just that.:)

---

### Post by davesmith on 2010-12-05
Well if you are enjoying it so much how about contributing something constructive then? Compiling source code looks jolly complicated particularly sorting out the dependencies. I might just have to wait till the pidgin developers release a LTS version.

---

### Post by amjjawad on 2010-12-05
> **uRock said:**
> Just running updates should have fixed his/her problem. **Hopefully the lack of response means that it did just that**.:)

Ditto :D

---

### Post by davesmith on 2010-12-05
Bug's idea works for MSN at the moment. d/l the msn certificate from
[http://www.webupd8.org/2010/11/fix-pidgin-msn-omegacontactsmsncom.html](http://www.webupd8.org/2010/11/fix-pidgin-msn-omegacontactsmsncom.html)
and replace the certificate in the purple file. Re-start pidgin and it works - but not for aim or icq

If i find a solution to this pidgin upgrade issue for 8.04 I'll post the solution. My thanks to Bug and those who posted useful ideas and code to try

---

### Post by amjjawad on 2010-12-05
> **davesmith said:**
> Well if you are enjoying it so much how about contributing something constructive then? 

1) I don't want to get in the way as someone else is helping you already :)

2) I've never ever seen or used 8.10 before so I'll never act as I did ;)

3) This thread is not our thread. I know I  did the same that you did, post my own problem here but it's highly recommended to start a new thread. I posted because I have 10.04 which is close to 10.10 and have exactly the same issue. Starting a new thread will make it easier to follow and posting on an existing thread will make it harder to everyone. Again I know I did that but I'm just saying what's right :)
Don't get me wrong, but I like to be clear and honest :)

Please don't be offended, I'm just explaining my situation :)

GOOD LUCK :D

---

### Post by uRock on 2010-12-05
What more could I do short of SSHing to your machine and running the commands for you? The link I posted earlier only requires running 5 commands, then the program will be installed.

I am just as aggravated as you are that MSN keeps making changes to the application. I recently updated MSN messenger in Windows 7 and I see where the problems came from as they have turned the IM into a social client that was so cluttered that I uninstalled it with the plan to never use MSN messenger in Windows ever again. In the end they do manage to keep the level of spam bots down and that is the only reason I stick with them in Pidgin.

---

### Post by davesmith on 2010-12-05
We live in interesting times - unfortunately in this age of cyberwarfare IM apps have obvious uses to those with malign intent. Encrypting coms is bound to attract the attention of homeland security people, but some of us value privacy and believe in an un-alienable right to communicate without some faceless aparatchik monitoring what is said.

Maybe MSN are coding a backdoor into Messenger to make it easier for the spooks to check you are not hosting Wikileaks somewhere LOL

---

### Post by uRock on 2010-12-05
> **davesmith said:**
> We live in interesting times - unfortunately in this age of cyberwarfare IM apps have obvious uses to those with malign intent. Encrypting coms is bound to attract the attention of homeland security people, but some of us value privacy and believe in an un-alienable right to communicate without some faceless aparatchik monitoring what is said.

Maybe MSN are coding a backdoor into Messenger to make it easier for the spooks to check you are not hosting Wikileaks somewhere LOL

Lol. I totally agree with the need to keep things as secure as possible.

I tried the commands on the supposed easy link and it wasn't so easy. It would still require creating the launcher. I have installed a tarball to the home folder before, but it runs a major security issue because it can run updates without sudo. If you want, I can type up directions to do so, but as I said it isn't the safe way to go.

---

### Post by amjjawad on 2010-12-06
Hey guys, guess what? after I updated Pidgin to 2.7.7 [SIZE=3](libpurple 2.7.7) as described earlier in this thread, I noticed there is another issue :(

Pidgin just disappears by itself without I do anything. It's running and I'm online, not even chatting with anyone (I have only one MSN account configured, that's all) and out of sudden, it disappears. I wonder if anyone else has the same issue? do I have to start a new thread? any advice?

P.S.
Disappear = turn off all by itself.
[/SIZE]

---

### Post by karthick87 on 2010-12-06
Just start a new thread.It will be easier for you to get answers quickly.

---

### Post by amjjawad on 2010-12-06
> **karthick87 said:**
> Just start a new thread.It will be easier for you to get answers quickly.

I'll keep monitoring Pidgin and if that problem will happen again, guess I have no other choice but to start a new thread.

---

