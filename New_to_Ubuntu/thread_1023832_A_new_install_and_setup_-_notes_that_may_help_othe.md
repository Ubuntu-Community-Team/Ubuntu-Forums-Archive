---
title: "A new install and setup - notes that may help others"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by blueridgedog on 2008-12-28
I just completed what is turning out to be an annual re-install of Ubuntu during my Christmas leave and as usual, I kept notes on the steps I used to customize the base install to a point that I consider ready to go (for my purposes).  I do this re-install not because my Ubuntu system needs it, but in order to sample the state of the art so to speak in desktop Linux and what is required for a simple user to get a system that will work for every day tasks (again, my everyday tasks...yours may vary).

I thought I would share the post-install steps so that others may benefit (in the event that they see something they are struggling with or want to install or have a suggestion to make to me for a better way to solve a problem).

If you elect to try any of the steps that I took, read the documentation I link to completely, as your system may differ and you should know the rational behind what you are doing rather than simply copying and pasting code from websites.  Each of the documentation sites really explains a great deal about the process.

First I enabled the restricted driver for my ATI card (either the icon in the system tray or System -> Administration -> Hardware Drivers)

I then updated Ubuntu (the update icon should be in the system tray after a new install, if not System -> Administration -> Update Manager).

Once the initial update was complete I installed ad-block plus on Firefox.  This is essential in my life.  Read more at: [http://adblockplus.org/en/](http://adblockplus.org/en/) After you install the plugin and Firefox restarts, you will need to subscribe to a filter set that matches your language.

The next step was to enable Ubuntu to display some of the content I use for which there is no free codec or product.  Documented at: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

sudo apt-get install ubuntu-restricted-extras

Documented at: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update
sudo apt-get install medibuntu-keyring
sudo apt-get update
sudo apt-get install libdvdcss2
sudo apt-get install w32codecs
sudo apt-get install ttf-xfree86-nonfree

The above installed the non-free restricted extras and the tools needed to play most any file type.  The Medibuntu page is essential reading.

Though not relevant for all users, I keep my "documents" on a separate drive so that I can simply mount that drive in various OS's that I use.  During the install I had elected to mount that drive as /documents.

To make Ubuntu use the drive and the mount point /documents as my "Documents" in Nautilus I did the following
rm -rf /home/MYUSERNAME/Documents ##MAKE CERTAIN YOU HAVE NOT PUT ANYTHING HERE
ln -s /documents/ ./Documents 

In order to be the owner of all the files in /documents when it was mounted I had to edit /etc/fstab:

UUID=D455-4CF6  /documents      vfat    defaults,utf8,umask=007,gid=1000,uid=1000 0       1

What was added was my gid and uid so that when mounted I owned all of the files.

The version of OpenOffice that installed was not the current (and impressive I must say) 3.0, so I added:

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

To Software sources to upgrade OpenOffice and allowed Ubuntu to update the associated OpenOffice programs.  To do this you can select System -> Adinistration -> Software Sources and then select "Third-Party Software and click Add and paste the line in.  This process is documented at:
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml).

Once the new software source was keyed in, Ubuntu updated to OpenOffice 3.0 via the normal update process. 

I added Banshee for Ipod use using synaptic (System -> Administration -> Synaptic Package Manager), but it choked on m4b files (these are audio books and I have many).

After researching the audio book problem, I realized that the version installed from the Ubuntu repositories was outdated, so I added:


deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) intrepid main

To software sources to get latest banshee which worked.  As above, you can select System -> Administration -> Software Sources and then select "Third-Party Software" and click Add and paste the line in.  As soon as you add this software source, Ubuntu will update Banshee just like it did OpenOffice above.

I have two windows programs that I use frequently and they run great under wine, so I installed wine with:

sudo apt-get install wine

I also have some tools that I use that I need to build, so I installed the essential build tools with:

sudo apt-get install build-essential 

I noticed that my video performance was choppy (wmv and mpegs) so I tried tweaking the ATI driver with:

sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

But this made no change.  I solved the problem by dropping my visual effects to "none" (System -> Preferences -> Appearance &#8594; visual effects).

This solved the choppy video playback and once again I made a mental note to pick up an nvidia card for this system because the ATI product is much less supported.

(If you have suggestions about this, let me know)

That pretty much was the extent of my customization and I must admit that 8.10 is impressive.  There is a fit and finish to the OS that wows me.  

I also can't say enough good about OpenOffice 3.0.  To have this OS and an office suite as part of our FOSS options is amazing.

---

### Post by hermes0710 on 2008-12-28
Hi and merry Christmas.
 The choppy video is met in Nvidia cards too. What i have found so far as a solution is to disable compiz :(

---

### Post by blueridgedog on 2008-12-28
I suspect you are right, but I may pickup a cheap nvidia card just to try.  I have used ATI forever, but have nothing against another brand.  I do wish we could get better graphics support the the big two chip makers.

---

