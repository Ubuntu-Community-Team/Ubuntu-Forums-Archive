---
title: "ubuntu multimedia codes???"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by basics on 2009-04-26
Hi,

I am proud to say I have been an ubuntu user just over a year now.  [I]love ubuntu and I would never go back to windows. I have not had windows on my PC since this time last year. I have not missed it at all eccept for one problem that makes me wish I had windows on my machine.

I am never able to play wmv on my machine or other major file types. I don't know anything about this stuff but I know when I want to watch a TV station on the interenet ASX works fine for me.

I am not a geek, so I don't want to download every package in the world to my machine. I just want my machine to work like any other basic computer that does not have issues with playing different formats. 

Help! :)

Just so you all know I just upgraded to 9.04. I have had this issue ever since I started with ubuntu. When 8.04 was released I started to use ubuntu.

Thanks...
[/I]

---

### Post by feelshift on 2009-04-26
Have you installed the ubuntu-restricted-extras package from the medibuntu repository?

---

### Post by oldos2er on 2009-04-26
The program vlc should be able to handle wmv "out of the box."

---

### Post by Wiebelhaus on 2009-04-26
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by steve101101 on 2009-04-26
Enable mediubuntu repositories to get more codecs.

---

### Post by Wiebelhaus on 2009-04-26
> **steve101101 said:**
> Enable mediubuntu repositories to get more codecs.

Please , Let's not assume they know what we are talking about and provide links , quotes , code or other relevant information.

Thanks.

[http://www.medibuntu.org/](http://www.medibuntu.org/)

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

> Introduction

Medibuntu (Multimedia, Entertainment & Distractions In Ubuntu) is a repository of packages that cannot be included into the Ubuntu distribution for legal reasons (copyright, license, patent, etc).

Some of these packages include the libdvdcss package from VideoLAN and the external binary codecs package (commonly known as w32codecs) used by MPlayer and xine.

Disclaimer

Patent and copyright laws operate differently depending on which country you are in. Please obtain legal advice if you are unsure whether a particular patent or restriction applies to a media format you wish to use in your country.

See Ubuntu's Free Software Philosophy and the FreeFormats page for a more comprehensive discussion of these issues.

Free and Non-free Components

Medibuntu has two components for its repository. They are labelled free and non-free. The free component has the packages for software whose sources are made freely and/or are distributed with an open source license such as the GNU General Public License. The non-free component contains software whose sources are not made freely available and/or are distributed with a license that restricts certain ways the software can be distributed.

Software in the free component are not distributed in the Ubuntu repositories because of legal issues with that software in certain countries. Some software such as Amarok and Kaffeine are distributed through the main Ubuntu repositories but with certain functionalities taken away, again because of legal issues. Medibuntu distributes these kind of packages with those functionalities in place.

Software in the non-free component are not distributed in the main Ubuntu repositories because of the licenses that these software are distributed with restricts how they can be distributed. The software in the non-free component are usually not needed for general use as there are alternatives or implementations in other open source licensed software. Some software, such as Google Earth and Adobe Acrobat Reader, are available directly from the company's website that owns the rights to them.

Since the packages in the non-free component are usually not needed, the instructions in the next section will include a step to exclude acquiring package information from the non-free component of the Medibuntu repository.

Adding the Repositories

Below are the instructions to add the Medibuntu repository to your system's list of APT repositories. These are commands that should be run in the Terminal (Applications -> Accessories -> Terminal).

If you are new to Ubuntu, please see [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) for an overview of repositories.

Add Medibuntu to your sources.list, as well as its GPG key to your keyring. Make sure to use the correct sources.list that corresponds to your current distribution.

    *

      Any Ubuntu Release and keyring:

      sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

    *

      Ubuntu 9.04 "Jaunty Jackalope":

      sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

    *

      Ubuntu 8.10 "Intrepid Ibex":

      sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

    *

      Ubuntu 8.04 "Hardy Heron":

      sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

    *

      Ubuntu 7.10 "Gutsy Gibbon":

      sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

    *

      Ubuntu 6.06 "Dapper Drake":

      sudo wget [http://www.medibuntu.org/sources.list.d/dapper.list](http://www.medibuntu.org/sources.list.d/dapper.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

Then, add the GPG Key:

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

You may be asked to accept this package even though it cannot be authenticated. This is normal; typing "Yes" means you trust Medibuntu.

Optional step : remove the non-free component

Some people don't want to install non-free software on their computer as explained in the "Free and Non-Free components" section. We will explain how to exclude getting packages from the non-free component of the Medibuntu repository.

You should understand that if you remove the non-free component, you will NOT have access to these packages:

    * acroread (Acrobat Reader -- not really needed because you can use free software, such as Evince, to read pdfs)
    * alsa-firmware -- needed for some audio cards
    * AMR and FAAC support in MPlayer and FFmpeg
    * googleearth
    * restricted video codecs (ppc-codecs, w32codecs, w64codecs)
    * Skype 

the complete list of packages is here.

To exclude getting packages from the non-free component of the Medibuntu repository, type the following command:

sudo sed -e 's/ non-free//' -i /etc/apt/sources.list.d/medibuntu.list

Installing Individual Packages

Most Ubuntu users will only require a few packages from the Medibuntu repository; nonetheless, it's easier simply to add the repository to your setup as detailed above. The most common packages are libdvdcss2 for playing DVDs and the non-native codecs packages (w32codecs, w64codecs, ppc-codecs) for playing non-native media formats. If you wish to install individual packages, then follow the steps below.

    *

      With your favourite web browser, go to [http://packages.medibuntu.org/](http://packages.medibuntu.org/).
    * Choose the Ubuntu version you're currently using.
    * Find the package for your architecture in the listing, and save it to your personal directory on your hard drive. You may need to also download any dependencies that are also in medibuntu.
    * Right click on the package you just downloaded.
    * Select Ubuntu Package Menu.
    * Choose Install Package. 

Playing Encrypted DVDs

To play encrypted DVDs, the libdvdcss2 package is essential. libdvdcss is a simple library designed for accessing DVDs like a block device without having to bother about the decryption. Some more information about this package can be found at [http://www.videolan.org/developers/libdvdcss.html](http://www.videolan.org/developers/libdvdcss.html).

Below are the instructions for installing the packages using the command line. For other methods, please refer to Installing Software.

With the entire Medibuntu repository

If you have added the entire Medibuntu repository, you just need to install the package using APT:

sudo apt-get install libdvdcss2

With individual packages

If your wish to install just libdvdcss2, you can first download the individual package and then install the package.

    *

      i386:

      wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb)
      sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb

    *

      amd64:

      wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb)
      sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb

    *

      powerpc:

      wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu2_powerpc.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu2_powerpc.deb)
      sudo dpkg -i libdvdcss2_1.2.9-2medibuntu2_powerpc.deb

Playing Non-Native Media Formats

There are a few formats such as certain Windows formats, Real, and Apple Quicktime which do not have native codecs under Linux. To work around this issue, external binary codecs are used instead to play these formats. MPlayer and xine use such external codecs and these codecs are stored in the MPlayer website in their codecs directory located at [http://www.mplayerhq.hu/MPlayer/releases/codecs/](http://www.mplayerhq.hu/MPlayer/releases/codecs/).

Medibuntu distributes a package which contains these codecs. The codecs are under the non-free component of the repository. If you followed the directions above to exclude the non-free component, follow the steps again to add the Medibuntu repository to your system's list of APT repositories and skip the step to exclude the non-free component.

Below are the instructions for installing the packages using the command line. For other methods, please refer to Installing Software.

With the entire Medibuntu repository

If you have added the entire Medibuntu repository, install the package using APT.

    *

      For i386, the package is called w32codecs:

      sudo apt-get install w32codecs

    *

      For amd64, the package is called w64codecs:

      sudo apt-get install w64codecs

    *

      For ppc, the package is called ppc-codecs:

      sudo apt-get install ppc-codecs

    *

      NOTE: This ppc-codecs package is currently only available for edgy and feisty. These codecs are also available from MPlayer and can be downloaded directly from [http://www.mplayerhq.hu/MPlayer/releases/codecs/all-ppc-20061022.tar.bz2](http://www.mplayerhq.hu/MPlayer/releases/codecs/all-ppc-20061022.tar.bz2).
    *

      NOTE 2: the w64codecs is only made for feisty and later, so not for dapper or edgy
    *

      NOTE 3: the w32codecs can be used on amd64 ubuntu (hardy, intrepid) with the i386 mplayer, but it requires manual installation and forcing the install. The i386 mplayer executable can be extracted (and moved or renamed to mplayer32 to keep it separate from the 64 bit version), and will use the ia32 /usr/lib32 entries and w32 codecs - but updated libraries (e.g. libx264.so.59 v.s .57) may also be required. 

With individual packages

If you wish to install just the individual external codecs package, you can first download the individual package and then install the package.

    *

      For i386, the package is called w32codecs:

      wget -c [http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb)
      sudo dpkg -i w32codecs_20071007-0medibuntu2_i386.deb

    *

      For amd64, the package is called w64codecs:

      wget -c [http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20071007-0medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20071007-0medibuntu1_amd64.deb)
      sudo dpkg -i w64codecs_20071007-0medibuntu1_amd64.deb

    *

      For ppc, the package is called ppc-codecs:

      wget -c [http://packages.medibuntu.org/pool/non-free/p/ppc-codecs/ppc-codecs_20071007-0medibuntu1_powerpc.deb](http://packages.medibuntu.org/pool/non-free/p/ppc-codecs/ppc-codecs_20071007-0medibuntu1_powerpc.deb)
      sudo dpkg -i ppc-codecs_20071007-0medibuntu1_powerpc.deb



---

### Post by sundar_ima on 2009-04-28
> **feelshift said:**
> Have you installed the ubuntu-restricted-extras package from the medibuntu repository? if you do not have an internet connection download and install ubuntu restricte extras 9.04 from here [http://rapidshare.com/files/226569752/Ubuntu_Restricted__Extras_9.04_Offline_Installer.tar.gz]("http://rapidshare.com/files/226569752/Ubuntu_Restricted__Extras_9.04_Offline_Installer.tar.gz") follow the simple instructions given in the "read me" text file.

---

### Post by leogets on 2009-04-29
Hello,
 
Sundar_ima is the link you provided above for MOVIE\MULTIMEDIA CODECS or not?
 
I am very new to Ubuntu. I downloaded the latest version 9.0.4.
 
It came with a Movie player, BUT NO CODECS.
I went to play some of the movies I have and none of them would play.
The majority of them use the XviD codec v1.0.3 -1.1.2 Final they use a variant of AC3, MP3, MP3 Lame for the Audio..... VERY STANDARD FORMATS FOR VIDEOS.
 
Why did Ubuntu not come with a codec pack installed...
 
I been clicking on various links to download a media codec pack for linux...
 
For windows, I have no problems what-so-ever. I goto K-Lite find the codec pack for windows and I'm able to download it without any problems.
Trying to even find a place with a "DOWNLOAD LINK" is a pain in the ***. Almost an hour I've spent already trying to find a "DOWNLOAD LINK" where I can actually download a codec pack and I have not been able to even accomplish that.
 
Why are these codecs NOT made easily findable to download.
 
I found plenty of sites the say download, when I actually hit the link I am presented with another page with tons of reading BUT NO ACTUAL LINKS TO DOWNLOAD THE FILE NEEDED. 
 
So, WHERE CAN I DOWNLOAD A CODED PACK FOR Linux UBUNTU?
 
Codec packs have changed very little in the last while. Most of my movies are .avi, some .mkv files and .srt for subtitles as is most others who view movies.
I can still go back to using a K-Lite Codec Pack 1.63 and still all of my movies will play just fine in windows.
 
Why did Ubuntu not include the latest codec pack and why is something that should be so easy to find so hard?
 
Thanks for any help in getting a fix for this.

---

### Post by alphacrucis2 on 2009-04-29
> **leogets said:**
> Hello,
 
I am very new to Ubuntu. I downloaded the latest version 9.0.4.
 
It came with a Movie player, BUT NO CODECS.
I went to play some of the movies I have and none of them would play.
The majority of them use the XviD codec v1.0.3 -1.1.2 Final they use a variant of AC3, MP3, MP3 Lame for the Audio..... VERY STANDARD FORMATS FOR VIDEOS.
 
Why did Ubuntu not come with a codec pack installed...
 
I been clicking on various links to download a media codec pack for linux...
 
For windows, I have no problems what-so-ever. I goto K-Lite find the codec pack for windows and I'm able to download it without any problems.
Trying to even find a place with a "DOWNLOAD LINK" is a pain in the ***. Almost an hour I've spent already trying to find a "DOWNLOAD LINK" where I can actually download a codec pack and I have not been able to even accomplish that.
 
Why are these codecs NOT made easily findable to download.
 
I found plenty of sites the say download, when I actually hit the link I am presented with another page with tons of reading BUT NO ACTUAL LINKS TO DOWNLOAD THE FILE NEEDED. 
 
So, WHERE CAN I DOWNLOAD A CODED PACK FOR Linux UBUNTU?
 
Codec packs have changed very little in the last while. Most of my movies are .avi, some .mkv files and .srt for subtitles as is most others who view movies.
I can still go back to using a K-Lite Codec Pack 1.63 and still all of my movies will play just fine in windows.
 
Why did Ubuntu not include the latest codec pack and why is something that should be so easy to find so hard?
 
Thanks for any help in getting a fix for this.

The "fix" has already been given further up the thread. I believe Ubuntu don't distribute them because of legal issues. Read the earlier post about medibuntu.

---

### Post by leogets on 2009-04-29
Hello Sundar_ima,
 
This is the contents of Readme.txt file contained within the Ubuntu_Restricted__Extras_9.04_Offline_Installer.tar.gz
file that you uploaded.
 
Is this a MOVIE PLAYER CODEC PACK or not?
From what I can see it primarily says things about AUDIO Codecs but Nothing in reguards to VIDEO CODECS.
 
It says "3. Enter your password in Terminal (if it asks)"
where do I get this password?
 
 
 
===================================================
Readme.txt file:
===================================================
 
***************************************
Thank you for downloading this package.
***************************************
Installing this package will pull in support for MP3 playback and decoding,
support for various other audio formats (GStreamer plugins),Java runtime environment, 
Flash plugin, LAME (to create compressed audio files), and DVD playback.
Please note that this does install libdvdcss2, and will let you play encrypted DVDs.
But Microsoft Fonts should be installed manually. See the instructions below...
###############################
Installing Restricted Packages
###############################
1. Double click on the "install.sh" file
2. In the new will click "Run in Terminal"
3. Enter your password in Terminal (if it asks)
Thats it...
###########################
Installing Microsoft Fonts
###########################
1. Copy the fonts folder
2. paste it in your home folder (places--->> Home folder)
3. Rename fonts folder as .fonts
Thats it...

---

### Post by leogets on 2009-04-29
"The "fix" has already been given further up the thread. I believe Ubuntu don't distribute them because of legal issues. Read the earlier post about medibuntu."
 
And what legal issues are there?
I can download K-Lite Codec Pack Free of charge...
So there can't be any legal issues from my point of view.
And VLC Media Player already comes with video codes capable of playing pretty well all of the video media I have.  and again VLC Media Player is Free however you could donate if feel you like and use the program a lot which I don't, I've only tried it.  My preference for a movie player is Zoom Player.
No other Video player I have found so far offers the amount of control and versitlity that Zoom Player offers.
It is the best.

---

### Post by mikewhatever on 2009-04-29
> **leogets said:**
>  
And what legal issues are there?
I can download K-Lite Codec Pack Free of charge...
So there can't be any legal issues from my point of view.

Don't you think this is a bit egocentric? Canonical can't distribute patented codecs, no matter what you can or can not download.

---

### Post by leogets on 2009-04-29
Yes maybe, but there is quite a difference between being able to PLAY a movie that is made with a specific codec (Which these codecs should be made FREE) WHEREAS re/ENCODING A MOVIE (Where these codecs you should have to PAY for because you would like to use THIS SPECIFIC CODEC to ENCODE YOUR MOVIES WITH THEM).
 
The only blimp to the lot of video codecs that I see is the QuickTime - MPG encoding.
 
I guess that's why people nowadays stay away from that codec. Todays standards are pretty much based on the XviD and DivX codecs nobody really uses anything else.

---

### Post by mkvnmtr on 2009-04-29
If you will read the post above about the medibuntu repository it will tell you how to enable the repository. Then you lill have in your package manager every codec that you could need. You will just have to point and click to download and install them. You might need to read a little to find just which ones you might need. I can think of no simpler method in luse in any other os.

---

### Post by slakkie on 2009-04-29
Some members of a Dutch forum (forum.fok.nl) combined their usefulness and created this script to help others:

```

#!/usr/bin/env bash

# Check if we are on Ubuntu
if [ "$(lsb_release -si)" != "Ubuntu" ] ; then
    echo "This script is only intended to run on Ubuntu"
    exit 255
fi

# Check if we are root
if [ $UID -ne 0 ] ; then
    echo "Please run this as root!"
    exit 255
fi

sources=/etc/apt/sources.list

# Get distro
distro=$(lsb_release -sc)

# Check if medibuntu repo is already present
grep -v "^#" $sources | grep "medibuntu" &>/dev/null

if [ $? -ne 0 ] ; then
    # Add them if not and update
    cat <<OEF >> $sources

# Medibuntu repositories, check http://www.medibuntu.org/ for more details
deb http://packages.medibuntu.org/ $distro free non-free
OEF

    wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | apt-key add -
    aptitude update
fi

# Finally, install all the packages
aptitude install gstreamer0.10-ffmpeg ubuntu-restricted-extras vlc mplayer mozilla-plugin-vlc mozilla-mplayer libdvdcss2 non-free-codecs


```

---

### Post by sundar_ima on 2009-04-30
> **leogets said:**
> Hello Sundar_ima,
 
This is the contents of Readme.txt file contained within the Ubuntu_Restricted__Extras_9.04_Offline_Installer.tar.gz
file that you uploaded.
 
Is this a MOVIE PLAYER CODEC PACK or not?
From what I can see it primarily says things about AUDIO Codecs but Nothing in reguards to VIDEO CODECS.
 
It says "3. Enter your password in Terminal (if it asks)"
where do I get this password?
 
 
 
===================================================
Readme.txt file:
===================================================
 
***************************************
Thank you for downloading this package.
***************************************
Installing this package will pull in support for MP3 playback and decoding,
support for various other audio formats (GStreamer plugins),Java runtime environment, 
Flash plugin, LAME (to create compressed audio files), and DVD playback.
Please note that this does install libdvdcss2, and will let you play encrypted DVDs.
But Microsoft Fonts should be installed manually. See the instructions below...
###############################
Installing Restricted Packages
###############################
1. Double click on the "install.sh" file
2. In the new will click "Run in Terminal"
3. Enter your password in Terminal (if it asks)
Thats it...
###########################
Installing Microsoft Fonts
###########################
1. Copy the fonts folder
2. paste it in your home folder (places--->> Home folder)
3. Rename fonts folder as .fonts
Thats it...

while installing ubuntu 9.04 you must have given password. that is the password you should give. this packages will allow you to play most widely used **video and audio** formats including **encripted dvd**.

---

### Post by psy-moon on 2009-05-02
Hi there all, I have followed the instructions given above and ...guess what...it works...That is I am now watching and hearing my DVDs on Mplayer. Thanks

---

