---
title: "Evince PDF Reader not working, how to install Acrobat?"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by BastardNamban on 2009-07-01
Trying to do my taxes (late) for the first time in Ubuntu. Evince document reader opens the IRS's PDFs just fine, and lets me edit them.

BUT IT WON'T LET ME SAVE ANY OF IT. I found this out the hard way- 3 hours of tax calculations destroyed, when I saved a copy, and all the entries I had made to the interactive/text field PDFs were GONE. So forgive me if I seem a bit insistent, but I am really, really pissed off right now. I don't want to deal with it anymore, googling gets me, as usual, sketchy answers at what's wrong here. Some results say it's a bug, some say saving editable PDF fields is only able as a feature in Adobe Acrobat. All I know is it doesn't work in Evince, and I lost my taxes because of it.

I have the sanity to do this ONE LAST TIME, and I've wanted Acrobat from the beginning anyway. Except nothing I try installs it! I have:```
/home/shogun/Desktop/AdobeReader_enu-8.1.5-1.i486.tar.bz2, AdbeRdr9.1.1-1_i486linux_enu.bin, & AdbeRdr10_en_US.exe
``` all on my desktop. Using the .tar.bz2 would be compiling from source, I don't want to **** with that. I want simple right now, before I lose my mind. Extracting the .bin file does nothing (```
shogun@Valhalla:~$ ./<AdbeRdr9.1.1-1_i486linux_enu>.bin
bash: AdbeRdr9.1.1-1_i486linux_enu: No such file or directory

```). 

Even using wine with the .exe registers NOTHING. Clicking it, trying to manually add it to wine through adding it to the /C folder, nothing happens.

I am losing my damn mind, and I'm ready to kill someone. I need to finish my taxes, and I'm sick of stupid glitches like this ruining an otherwise good linux experience so far. I will calm down if someone can help me with something that works!

---

### Post by colau on 2009-07-01
```

sudo aptitude install acroread

```

---

### Post by tvtech on 2009-07-01
[http://ubuntu-tutorials.com/2008/06/23/install-adobe-acrobat-reader-812-on-ubuntu-804/](http://ubuntu-tutorials.com/2008/06/23/install-adobe-acrobat-reader-812-on-ubuntu-804/)

this link shows how to get it.  

I'm not sure it's going to do what you want though.  you may need something that edits pdf documents as well. 

like pdf edit which can be grabbed from add/remove programs. 

this link is a simple how too and only requires you to enter three lines into a terminal.  

hope it helps sorry to hear your not having fun. I know the feeling.

---

### Post by BastardNamban on 2009-07-01
Colau, I forgot to mention one thing- I tried installing via your method earlier, except with "sudo apt-get install acroread", and I got a message saying that was replaced with Adoberead-jpn, or something to that effect. Meaning the Japanese version.

I'm bilingual with Japanese, so I was desperate- I have some Japanese repositories for my SCIM Japanese input setup, so maybe that was why it wouldn't give me English. I substituted what it said was available at the time, and apt-get installed that, supposedly. Nothing happened- then.

I just used what you gave me, and now I have an Adobe Reader 8 Installer under my office applications tab, with a gear icon, and clicking it brings up a Japanese message: ```
Acrobat Reader 8.1.4&#12399;&#12414;&#12384;&#12452;&#12531;&#12473;&#12488;&#12540;&#12523;&#12373;&#12428;&#12390;&#12356;&#12414;&#12379;&#12435;&#12290;
AdobeReader8.1.4&#26085;&#26412;&#35486;&#29256;&#12452;&#12531;&#12473;&#12488;&#12540;&#12521;&#12434;&#38283;&#22987;&#12375;&#12414;&#12377;&#12290;
&#12497;&#12483;&#12465;&#12540;&#12472;&#12434;&#12480;&#12454;&#12531;&#12525;&#12540;&#12489;&#12377;&#12427;&#12383;&#12417;&#12395;&#12289;&#12452;&#12531;&#12479;&#12540;&#12493;&#12483;&#12488;&#25509;&#32154;&#12364;&#24517;&#35201;&#12391;&#12377;&#12290;
&#25509;&#32154;&#12375;&#12390;&#12356;&#12394;&#12356;&#22580;&#21512;&#12399;&#12289;&#20808;&#12395;&#12493;&#12483;&#12488;&#12527;&#12540;&#12463;&#35373;&#23450;&#12434;&#34892;&#12387;&#12390;&#12367;&#12384;&#12373;&#12356;&#12290;
```,
Which basically translates to "Acrobat Reader 8.1.4 is not yet installed. To download the package, an internet connection is neccessary. In event of no connection, check your network settings preferences".

In any case, WTF? How can I get rid of this Japanese installer I somehow added, get the English one (English is my native language), and install this?

Sorry, I know, this complicates things. Believe me, having to use repositories from 2 different languages causes headache error messages for me all the time. Usually they don't affect anything, they just tell me a Japanese version of something couldn't be found. Here, it's messing things up, I think.

Ideas?

---

### Post by BastardNamban on 2009-07-01
Oh- here's what I got with your advice before I noticed that icon: ```
shogun@Valhalla:~$ sudo aptitude install acroread
[sudo] password for shogun: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No candidate version found for acroread
No candidate version found for acroread
The following packages have been automatically kept back:
  g++-4.2 libavcodec1d libavformat1d libavutil1d libawn0-trunk 
  libpostproc1d libstdc++6-4.2-dev libswscale1d linux-libc-dev mencoder 
  python-awn-trunk 
The following packages have been kept back:
  app-install-data-commercial awn-extras-applets-trunk cairo-dock 
  cairo-dock-plug-ins cpp-4.2 cron cupsys cupsys-bsd cupsys-client 
  cupsys-common ffmpeg file firefox-3.0 firefox-3.0-gnome-support 
  firefox-gnome-support foomatic-filters gcc-4.2 gcc-4.2-base 
  gstreamer0.10-esd gstreamer0.10-plugins-good 
  gstreamer0.10-plugins-good-dbg gstreamer0.10-plugins-good-doc gvfs 
  gvfs-backends gvfs-fuse libcupsimage2 libcupsys2 libdvdcss2 libffi4 
  libgcc1 libgomp1 libgvfscommon0 libmagic1 libmagick10 libpurple0 
  libsasl2-2 libsasl2-modules libssl0.9.8 libstdc++6 
  linux-headers-2.6.24-24 linux-headers-2.6.24-24-generic 
  linux-image-2.6.24-24-generic lsb-base lsb-release mplayer ntpdate 
  openssl pidgin pidgin-data pm-utils tzdata xulrunner-1.9 
  xulrunner-1.9-gnome-support 
0 packages upgraded, 0 newly installed, 0 to remove and 64 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
shogun@Valhalla:~$ 

```

---

### Post by BastardNamban on 2009-07-01
Tvtech, I tried that guide already. That was how I ended up with this Japanese installer somehow. After everything I did there, it said that app was no longer available/replaced with the japanese version. Hence my problem now.

I already tried getting PDFEDIT with synaptic. I don't have any damn clue how to use it, and my attempts were fruitless.

Look, I hate to invoke MS$, but downloading the SAME PDF's in XP from the IRS, opening them in Acrobat, lets me edit the open fields just like I can in Linux, but it lets me SAVE my changes, no problems. So it must be an Acrobat feature or something. That's why I want to try Acrobat in Ubuntu. That XP computer is no where near secure, riddled with viruses, and slow as molasses as the north pole. I won't use it unless I have to.

---

### Post by mbsullivan on 2009-07-01
So... To be crystal clear, you're saying that Adobe Reader under Linux does *not* do what you want? The command to run it is "acroread".

Adobe Acrobat costs money to buy under Windows... I'm not sure if it's available under Linux.

You're right, though. It can create (in addition to read) PDF files.

Mike

---

### Post by BastardNamban on 2009-07-01
> **mbsullivan said:**
> So... To be crystal clear, you're saying that Adobe Reader under Linux does *not* do what you want? The command to run it is "acroread".

Adobe Acrobat costs money to buy under Windows... I'm not sure if it's available under Linux.

You're right, though. It can create (in addition to read) PDF files.

Mike

I'm saying I WANT Adobe Reader in linux. That's all the XP box has. I don't have it in linux, and it apparently does do what I want- Evince is the one that erased my taxes, not adobe!

And now, I can't believe this- I'm having an asthma attack. I haven't had astma for almost 7 years- it had gone away completely. I was actually screaming so much in my frustration at linux, losing my taxes, and now all the **** keeping me from installing adobe reader properly, that I'm now choking. I need to get to a hospital- my lungs are choking me. I actually created my asthma again, somehow!

Please, someone, while I get help, please, try to help me here- or I'm going to end up screaming again when I come back. Linux has brought out my rage too much tonight, I can't believe this is happening.
excuse me.

---

### Post by BastardNamban on 2009-07-02
Update- I got medicine, calmed down. 2 shots of vodka helped my blood get enough oxygen to reset my lungs to normal.

I have a solution and a problem- it turned out, I was RIGHT- Adobe Reader, even in linux, lets you save changes to interactive PDFs with editable text fields- ie: the kind a LOT of people use, the tax forms from the IRS in PDF form.

You CAN save them in linux! But you need Adobe Reader to do it. It's a proprietary right, I guess, of using an editable PDF.

Problem- somehow, I got the Japanese version of Adobe Reader 8.1.4! I'm bilingual, so for now, I can do my taxes and save the changes. But I don't know how the version I got, described by above method with medibuntu sources, gave me the Japanese version.

It shows up in Synaptic as "adobereader-jpn 8.1.4~ja1". I was able to remove it here, but doing a search for adobe reader in Synaptic only turns it up again, and it's "adobereader-jpn-ipamonafont" option.
Why no English version? Is something wrong with my global sources list or something, that I'm missing?

Here's what I get doing the last step of the Adobe Reader install tutorial linked above: ```
shogun@Valhalla:~$ sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
[sudo] password for shogun: 
--01:03:50--  http://www.medibuntu.org/sources.list.d/hardy.list
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving www.medibuntu.org... 87.98.242.110
Connecting to www.medibuntu.org|87.98.242.110|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 276 [text/plain]

100%[====================================>] 276           --.--K/s             

01:03:51 (36.24 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [276/276]

shogun@Valhalla:~$ sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
Hit http://packages.medibuntu.org hardy Release.gpg
Ign http://packages.medibuntu.org hardy/free Translation-en_US                 
Hit http://us.archive.ubuntu.com hardy Release.gpg                             
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US                  
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US             
Hit http://packages.medibuntu.org hardy Release                                
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US              
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US            
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US    
Hit http://us.archive.ubuntu.com hardy-security Release.gpg                    
Hit http://repository.cairo-dock.org hardy Release.gpg                         
Ign http://repository.cairo-dock.org hardy/cairo-dock Translation-en_US        
Ign http://us.archive.ubuntu.com hardy-security/main Translation-en_US         
Hit http://archive.ubuntulinux.jp hardy/ Release.gpg                           
Ign http://archive.ubuntulinux.jp hardy/ Translation-en_US                     
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Get:1 http://ppa.launchpad.net hardy Release.gpg [307B]                        
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Get:2 http://ppa.launchpad.net hardy Release [27.6kB]                          
Ign http://us.archive.ubuntu.com hardy-security/restricted Translation-en_US   
Hit http://packages.medibuntu.org hardy/free Packages                          
Hit http://repository.cairo-dock.org hardy Release                             
Ign http://us.archive.ubuntu.com hardy-security/universe Translation-en_US     
Ign http://us.archive.ubuntu.com hardy-security/multiverse Translation-en_US   
Hit http://us.archive.ubuntu.com hardy Release                                 
Hit http://us.archive.ubuntu.com hardy-updates Release                         
Get:3 http://ppa.launchpad.net hardy Release [27.6kB]                          
Get:4 http://ppa.launchpad.net hardy Release [65.9kB]                          
Hit http://packages.medibuntu.org hardy/non-free Packages                      
Ign http://ppa.launchpad.net hardy Release                                     
Hit http://repository.cairo-dock.org hardy/cairo-dock Packages                 
Hit http://us.archive.ubuntu.com hardy-security Release                        
Hit http://archive.ubuntulinux.jp hardy/ Release                               
Hit http://us.archive.ubuntu.com hardy/main Packages                 
Hit http://us.archive.ubuntu.com hardy/restricted Packages           
Hit http://us.archive.ubuntu.com hardy/main Sources                  
Hit http://us.archive.ubuntu.com hardy/restricted Sources            
Hit http://us.archive.ubuntu.com hardy/universe Packages             
Ign http://ppa.launchpad.net hardy/main Packages                     
Hit http://us.archive.ubuntu.com hardy/universe Sources              
Hit http://us.archive.ubuntu.com hardy/multiverse Packages           
Hit http://us.archive.ubuntu.com hardy/multiverse Sources            
Hit http://us.archive.ubuntu.com hardy-updates/main Packages         
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages   
Hit http://us.archive.ubuntu.com hardy-updates/main Sources          
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources    
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages     
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources      
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages   
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources    
Ign http://archive.ubuntulinux.jp hardy/ Packages                    
Ign http://ppa.launchpad.net hardy/main Packages                     
Hit http://us.archive.ubuntu.com hardy-security/main Packages        
Hit http://us.archive.ubuntu.com hardy-security/restricted Packages  
Hit http://us.archive.ubuntu.com hardy-security/main Sources         
Hit http://us.archive.ubuntu.com hardy-security/restricted Sources   
Hit http://us.archive.ubuntu.com hardy-security/universe Packages    
Hit http://us.archive.ubuntu.com hardy-security/universe Sources     
Hit http://us.archive.ubuntu.com hardy-security/multiverse Packages  
Hit http://us.archive.ubuntu.com hardy-security/multiverse Sources   
Hit http://ppa.launchpad.net hardy/main Packages                     
Hit http://ppa.launchpad.net hardy/main Sources
Hit http://archive.ubuntulinux.jp hardy/ Packages
Hit http://ppa.launchpad.net hardy/main Packages
Hit http://ppa.launchpad.net hardy/main Packages
Fetched 310B in 1s (195B/s)
W: GPG error: http://ppa.launchpad.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
shogun@Valhalla:~$ sudo apt-get install acroread
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
shogun@Valhalla:~$ sudo apt-get install acroread
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  adobereader-jpn
E: Package acroread has no installation candidate
shogun@Valhalla:~$ 
shogun@Valhalla:~$ sudo apt-get install acroread
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  adobereader-jpn
E: Package acroread has no installation candidate
shogun@Valhalla:~$ 
```

---

### Post by -kg- on 2009-07-02
This is very odd.  You mentioned the packages that you have available from your repositories:

> It shows up in Synaptic as "adobereader-jpn 8.1.4~ja1". I was able to remove it here, but doing a search for adobe reader in Synaptic only turns it up again, and it's "adobereader-jpn-ipamonafont" option.

I have the Medibuntu repositories installed as well, so I launched Synaptics and searched for those two programs.  I don't have them.  I have acroread (which is installed) and acroread-fonts (which is not, but in the description it says that it has Japanese fonts, as well as a few others).

I notice that you are using Hardy (I'm using Jaunty) but that shouldn't make a difference as far as this is concerned.  I only have one thought...

You say you are bi-lingual, with Japanese as your second language.  Your information block says that you live in Pittsburg.  Did you by any chance specify (or otherwise get connected to) a repository server in Japan?  You can check this by launching "System/Administration/Software Sources" and checking your download source about halfway down the window on the first tab.

That's the only thing I can think of as to why you don't have the English version, and I don't have the Japanese version.  Perhaps the packages available are different from servers in different countries.

---

### Post by InfectedWithDrew on 2009-07-02
I'm wholly surprised that I haven't seen this already offered as a solution:

Download the .deb from Adobe's site.

Here's a convenient link for you to use, even... [http://get.adobe.com/reader/](http://get.adobe.com/reader/)

I hope this works for you, BN.

---

### Post by sanika on 2009-07-02
You can download the latest version of acroread from [ftp://ftp.adobe.com/pub/adobe/reader/unix/9.x/9.1.2/](ftp://ftp.adobe.com/pub/adobe/reader/unix/9.x/9.1.2/). There is an excellent post about installer formats [http://blogs.adobe.com/acroread/](http://blogs.adobe.com/acroread/). The post mentions the commands to be used for different installers. For the .bin installer, do the following:

   chmod +x AdbeRdr9.1.2-1_i486linux_enu.bin 
  ./AdbeRdr9.1.2-1_i486linux_enu.bin --install_path=<path_where_you_want_to_install_acroread>. By default, acroread will be installed inside /opt. 

-Sanika

---

### Post by BastardNamban on 2009-07-02
Guys, I already tried downloading from adobe's site- I had all the files- see my first post! Thus, chmod +x AdbeRdr9.1.2-1_i486linux_enu.bin, with it on the desktop, is giving me an error saying it can't find it. I tried putting it in the home directory and trying again, same error.

So I don't know why this won't install even though I have it!

I checked my software sources, and I am set to download from US servers.
However, under the "Authentication" tab, I have the Ubuntu-ja Archive Automatic Signing Key. Could this be a reason?

See my first post- I had the correct .bin file, and did the above operation again with chmod, and it can't find it, and nothing installs. A later post
shows doing "sudo apt-get install acroread" tells me that that version has been replaced with the Japanese version, therein named. Searching for Adobe Reader with medibuntu installed in Synaptic Package Manager too still only brings up the Japanese version for me, and nothing else.

Thus, something is wrong somewhere in telling my computer what to grab or show as available in only giving me the Japanese version. So I still don't know why. I'm about to just use the Japanese Adobe Reader to finish my taxes, inputing in English, and saving the changes- it works with Adobe Reader (Japanese version), I checked already. I may just use that for now unless someone has a better idea!

---

### Post by philinux on 2009-07-02
Click the medibuntu link below, follow all instructions to enable their repo.

Then acroread can be installed via add/remove, synaptic or from firefox address bar

apt://acroread

---

### Post by BastardNamban on 2009-07-02
> **philinux said:**
> Click the medibuntu link below, follow all instructions to enable their repo.

Then acroread can be installed via add/remove, synaptic or from firefox address bar

apt://acroread

Yes, I did this already. Now, again. 3-4 times. It's not that I don't understand how to get it- it's that the ONLY VERSION SHOWING UP IS JAPANESE.
I can't believe I have to say this again- PLEASE READ THE INITIAL POSTS.

Synaptic is normally great, but is only showing me the Japanese version of Acrobat Reader. I have all the English files direct from Adobe's site on my desktop, but the computer doesn't recognize them/accept that they are there when I go to install them.

Anyone, if you answer again, explain why I can only get the Japanese version, please. Don't instruct me on how to enable Medibuntu, I know how- that's the point. I know how to install the reader with synaptic. That's not the point either. I want the ENGLISH VERSION. I'm only getting access to the Japanese version. That's my problem!

---

### Post by Chronon on 2009-07-02
> **InfectedWithDrew said:**
> I'm wholly surprised that I haven't seen this already offered as a solution:

Download the .deb from Adobe's site.

Here's a convenient link for you to use, even... [http://get.adobe.com/reader/](http://get.adobe.com/reader/)

I hope this works for you, BN.

Try this advice.  Your initial post does not indicate that you did this.  

```
sudo dpkg -i *name_of_package*.deb
```

---

### Post by BastardNamban on 2009-07-03
```
shogun@Valhalla:~$ sudo dpkg -i AdbeRdr9.1.1-1_i386linux_enu.deb
[sudo] password for shogun: 
dpkg: error processing AdbeRdr9.1.1-1_i386linux_enu.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 AdbeRdr9.1.1-1_i386linux_enu.deb
shogun@Valhalla:~$
```

So, still, same problem. All the files on my desktop, yet none are recognized as existing.

I've long since run out of patience with this, as nothing is working.

Can anyone tell me WHY even in Synaptic the Japanese version is all that's coming up instead of the English one??? Could the medibuntu version I'm fetching be a Japanese one or something? I cannot understand why this insists on only showing the Japanese version available!

---

