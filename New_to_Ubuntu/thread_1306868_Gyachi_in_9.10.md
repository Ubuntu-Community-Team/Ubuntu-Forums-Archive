---
title: "Gyachi in 9.10"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by nakama85 on 2009-10-30
Does anyone know how to get Gyachi working in Ubuntu 9.10. Is there a .deb for it or a way to make an older one work???

Thanks

---

### Post by mangkook on 2009-10-30
same here.. need 64bit version

---

### Post by spiderbatdad on 2009-10-30
the following command should add loell's ppa and key to your sources...then just open synaptic package manger and select it:
```
sudo add-apt-repository ppa:loell/ppa
```
I am presently using gyachi without problems.

---

### Post by nakama85 on 2009-10-30
> **spiderbatdad said:**
> the following command should add loell's ppa and key to your sources...then just open synaptic package manger and select it:
```
sudo add-apt-repository ppa:loell/ppa
```
I am presently using gyachi without problems.

thanks this worked

---

### Post by alidm on 2009-11-01
> **spiderbatdad said:**
> the following command should add loell's ppa and key to your sources...then just open synaptic package manger and select it:
```
sudo add-apt-repository ppa:loell/ppa
```
I am presently using gyachi without problems.

I receive the following error when trying to add the repository:

```

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv C23B005D874996DC8D03A3C0D0D3C959DB2035A6
gpg: requesting key DB2035A6 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

```

Any ideas?

---

### Post by dukebytes on 2009-11-01
This must be a comm error.  Mine did the same thing.  I would try again tomorrow / later and see if it works.

---

### Post by alidm on 2009-11-01
OK. I tried again today and it worked.
```

ali@leno:~$ sudo add-apt-repository ppa:loell/ppa
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv C23B005D874996DC8D03A3C0D0D3C959DB2035A6         
gpg: requesting key DB2035A6 from hkp server keyserver.ubuntu.com
gpg: key DB2035A6: "Launchpad PPA for Loell Anthony Erecre" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```

Now, the problem is that when I run
```

sudo apt-get update

```
it says
```

Ign http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US
Hit http://archive.canonical.com karmic Release.gpg
....

W: Failed to fetch http://ppa.launchpad.net/loell/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```
Seems like the repository has been changed or moved. Has anybody else experienced this recently?

---

### Post by dukebytes on 2009-11-01
Just happened to me too.  Hopefully they get this fixed.  Gyachi is the only thing that works for me with the web cam.

---

### Post by spiderbatdad on 2009-11-01
I do not get this error, however i failed to mention that when I originally ran the command I did get an error and looked at launchpad to discover the package had not been updated for karmic yet...so I opened software sources under System>>Administration>>Software Sources...
Then go to Other Software tab and click on loell's ppa...choose edit and replace the word karmic with the word jaunty...everything else will stay the same...your synaptic will be fine and it will only add the Gyachi from the jaunty repos. like so

```
 sudo apt-get update
Hit http://security.ubuntu.com karmic-security Release.gpg
Ign http://security.ubuntu.com karmic-security/main Translation-en_US          
Hit http://us.archive.ubuntu.com karmic Release.gpg                            
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US                 
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US    
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US      
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US    
Hit http://security.ubuntu.com karmic-security Release                         
Hit http://archive.canonical.com karmic Release.gpg                            
Ign http://archive.canonical.com karmic/partner Translation-en_US    
**Hit http://ppa.launchpad.net jaunty Release.gpg**                                   
```

---

### Post by alidm on 2009-11-01
Jaunty repos worked for me too! Thanks spiderbatdad! :)

---

### Post by dukebytes on 2009-11-02
Worked for me too.  Thanks!!!

---

### Post by jesp8000 on 2009-11-07
> **spiderbatdad said:**
> the following command should add loell's ppa and key to your sources...then just open synaptic package manger and select it:
```
sudo add-apt-repository ppa:loell/ppa
```I am presently using gyachi without problems.

Hello Spiderbatdad, Glad to know it works for you.  How did you do that. I have a thread in here regarding this, and I said I installed gyachi in 9.10 without any errors or missing dependencies. When I run the gyachi, I can use my webcam but the voice chat is not. By the way, prior to installing gaychi, I installed lots of codec including those required by gyachi and I dont understand why voice chat doesnt work. Any suggestion about this?

---

### Post by wheatpenny on 2009-11-07
I am also having problems with voice chat not working. When I click on the voice chat icon a little square appears around it but nothing else happens. I've had this problem in both 9.04 and 9.10.  I posted about it in the Gyachi forum but got no answer.

---

### Post by spiderbatdad on 2009-11-07
Hi. I have never used the voice feature...only video text chat. My understanding is that voice only works in rooms. Have you tried voice chat in rooms? Perhaps a private room between two parties would work with voice chat. I know there have been many issues with voice. Sorry I can't be of more help. I am not a developer or maintainer, and I believe development is sadly coming to an end for Gyachi.

---

### Post by wheatpenny on 2009-11-07
Yes, in rooms is where I am having the problem. There is another person in the room I go to who is using the same version of Gyachi under the same version of Ubuntu and using the same voice codec pack, etc, but he doesn't have any problems with voice. Both of us are at a loss as to why it works for him but not for me.

---

### Post by ankscorek on 2009-12-20
what is the name of package in synaptic as my synaptic is not giving me any results for gyachi

---

### Post by rfdeshon on 2009-12-22
If you check the PPA page for loell it shows that the gyachi package failed to build for amd64 on the last update. No sign that anyone has attempted to fix this either.

you can grab the jaunty 64-bit package using this link though. I was able to install it without any problems on karmic and it works for me 
[https://launchpad.net/~loell/+archive/ppa/+files/gyachi_1.2.2-1~jaunty_amd64.deb](https://launchpad.net/~loell/+archive/ppa/+files/gyachi_1.2.2-1~jaunty_amd64.deb)

---

### Post by justinhj on 2010-01-05
> **nakama85 said:**
> thanks this worked

Thanks so much, I've been trying to get Gyachi working again for a while. I've been building it from the source on the developers site, and had trouble getting the webcam working. So glad there is working version.

---

### Post by raist1313 on 2010-01-23
> **rfdeshon said:**
> If you check the PPA page for loell it shows that the gyachi package failed to build for amd64 on the last update. No sign that anyone has attempted to fix this either.

you can grab the jaunty 64-bit package using this link though. I was able to install it without any problems on karmic and it works for me 
[https://launchpad.net/~loell/+archive/ppa/+files/gyachi_1.2.2-1~jaunty_amd64.deb](https://launchpad.net/~loell/+archive/ppa/+files/gyachi_1.2.2-1~jaunty_amd64.deb)
Thanks! This worked for me.

---

### Post by sougata on 2010-02-05
Hi , 

I am a beginner in UBUNTU 9.10 and absolutely loving it. I installed GYACHI IMPROVED 1.2.2 just 2 days ago and it was absolutely fine with webcam and other features. BUt just today , every time i am trying to login in my yahoo account , every time it is saying to me username or password nor valid. But i know it is perfectly OK as i can login into my yahoo account from meebo but consistently it is saying me here on GYACHI that this username or password is not valid.
I have re installed GYACHI but still not solved. I am also trying different servers but still problem going on.....I AM GETTING TIRED to exactly think what maybe the problem....

Can anyone tell me what the problem is going on...and how can i fix it ???

Cheers...

Sougata

---

### Post by rajeev1204 on 2010-02-05
I wouldnt recommend gyachi to anyone due to it being unmaintained long time at least from the website, last version was in 2007.

Its a serious security risk installing unmaintained software.

No offence to loell who maintains the packages and makes it work on each new release, but iam not sure if he or anyone else is working on the project.

---

### Post by loell on 2010-02-05
> **sougata said:**
> Hi , 

I am a beginner in UBUNTU 9.10 and absolutely loving it. I installed GYACHI IMPROVED 1.2.2 just 2 days ago and it was absolutely fine with webcam and other features. BUt just today , every time i am trying to login in my yahoo account , every time it is saying to me username or password nor valid. But i know it is perfectly OK as i can login into my yahoo account from meebo but consistently it is saying me here on GYACHI that this username or password is not valid.
I have re installed GYACHI but still not solved. I am also trying different servers but still problem going on.....I AM GETTING TIRED to exactly think what maybe the problem....

Can anyone tell me what the problem is going on...and how can i fix it ???

Cheers...

Sougata

try removing gyachrc   **rm ~/.yahoorc/gyach/gyachrc**

then try to log in again.

---

### Post by loell on 2010-02-05
> **rajeev1204 said:**
> I wouldnt recommend gyachi to anyone due to it being **unmaintained long time** at least from the website, last version was in 2007.

Its a serious security risk installing unmaintained software.

No offence to loell who maintains the packages and makes it work on **each new release,** but iam not sure if he or anyone else is working on the project.

emphasis mine ;) ,

though none taken,   yeah i agree, it's front page hasn't been updated for long time  now.

---

### Post by sports fan Matt on 2010-02-06
This above suggestion did not help.

---

### Post by loell on 2010-02-07
a fix has just been rolled out, v 1.2.4

if you are in karmic use this PPA repo

[https://launchpad.net/~baudm/+archive/ppa/+packages](https://launchpad.net/~baudm/+archive/ppa/+packages)

---

### Post by sougata on 2010-02-08
**** 	 	 
[B][I]try removing gyachrc   rm ~/.yahoorc/gyach/gyachrc

then try to log in again. 	[/I][/B] 

Hi , Loell i tried to do this also after installing the whole process and then running this command but it still shows the same problem. The thing which is bothering is that , how come it got logged in in the first day and then suddenly not logging in anymore??

Cheers , 

Sougata

---

### Post by Linuxforall on 2010-03-27
Big thanks to Loell and Bautista, I was unable to video chat with my wife who is currently in Philippines, the net cafe she goes to has issues with Skype and the MSN is too old to take webcams.

---

### Post by shinjan on 2010-04-03
I have installed gyachi 1.2.6 from the link [https://launchpad.net/~baudm/+archive/ppa/+packages]("https://launchpad.net/%7Ebaudm/+archive/ppa/+packages") today in ubuntu karmic...
im facing several problems in it:

1. Chat IDs are showing up in my buddy list not their names. I can see the names in pidgin.
2. How will I go to my inbox directly from gyachi?
3. The browser in-built inside gyachi is completely bull ****. Never works properly.
4. When it shows a buddy is online, if I refresh buddy list all buddies are shown offline immediately. Why?
5. Contacts never load in contacts tab. It always shows '0 address book contacts loaded'.

Any solutions to these problems?

---

### Post by loell on 2010-04-04
> **shinjan said:**
> I have installed gyachi 1.2.6 from the link [https://launchpad.net/~baudm/+archive/ppa/+packages]("https://launchpad.net/%7Ebaudm/+archive/ppa/+packages") today in ubuntu karmic...
im facing several problems in it:

1. Chat IDs are showing up in my buddy list not their names. I can see the names in pidgin.
2. How will I go to my inbox directly from gyachi?
3. The browser in-built inside gyachi is completely bull ****. Never works properly.
4. When it shows a buddy is online, if I refresh buddy list all buddies are shown offline immediately. Why?
5. Contacts never load in contacts tab. It always shows '0 address book contacts loaded'.

Any solutions to these problems?

1. feature needs to be requested.
2. existing and long time bug,  needs to be fix.
3. existing and long time bug,  needs to be fix.
4. existing bug,  needs to be fix. 
5. existing and long time bug,  needs to be fix.

you could help on discussion/testing at

[http://gyachi.sourceforge.net/](http://gyachi.sourceforge.net/)

thanks :)

---

### Post by matt3206 on 2010-04-15
Hi I got the following error after trying to install.

```
smith@laptop:~$ sudo apt-get update

bzip2: Data integrity error when decompressing.
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://af.archive.ubuntu.com karmic/universe Packages                                                                   
  Sub-process /bin/bzip2 returned an error code (2)
Hit http://af.archive.ubuntu.com karmic/universe Sources                                                                    
Hit http://af.archive.ubuntu.com karmic/multiverse Packages                                                                 
Hit http://af.archive.ubuntu.com karmic/multiverse Sources                                                                  
Get:17 http://af.archive.ubuntu.com karmic-updates/main Packages [197kB]                                                    
Get:18 http://af.archive.ubuntu.com karmic-updates/restricted Packages [14B]                                                
Get:19 http://af.archive.ubuntu.com karmic-updates/main Sources [59.3kB]                                                    
Get:20 http://af.archive.ubuntu.com karmic-updates/restricted Sources [14B]                                                 
Get:21 http://af.archive.ubuntu.com karmic-updates/universe Packages [125kB]                                                
Get:22 http://af.archive.ubuntu.com karmic-updates/universe Sources [29.7kB]                                                
Get:23 http://af.archive.ubuntu.com karmic-updates/multiverse Packages [7,354B]                                             
Get:24 http://af.archive.ubuntu.com karmic-updates/multiverse Sources [4,036B]                                              
Fetched 4,027kB in 9min 24s (7,130B/s)                                                                                      
W: Failed to fetch http://af.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

if some could help me "like a boss" i would be most appreciative.

Thanks
PUG:KS

---

