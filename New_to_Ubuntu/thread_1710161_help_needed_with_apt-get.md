---
title: "help needed with apt-get"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by nkdnkd on 2011-03-19
hi all,
I am a old fedora user.....who is migrating to ubuntu.
I am new to dpkg / apt-get / synaptic environment and got the following error during vlc installation :-
> nishith@nishith-Aspire-4720:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vlc : Depends: vlc-nox (= 1.1.4-1ubuntu1.4) but it is not going to be installed
       Depends: libavcodec52 (>= 4:0.6-1~) but it is not installable or
                libavcodec-extra-52 (>= 4:0.6-1~) but it is not installable
       Depends: libavutil50 (>= 4:0.6-1~) but it is not installable or
                libavutil-extra-50 (>= 4:0.6-1~) but it is not installable
       Depends: libqtcore4 (>= 4:4.7.0~beta1) but it is not installable
       Depends: libqtgui4 (>= 4:4.5.3) but it is not installable
       Depends: libsdl-image1.2 (>= 1.2.10) but it is not installable
       Depends: libtar but it is not installable
       Depends: libva-x11-1 but it is not installable
       Depends: libva1 but it is not installable
       Depends: libxcb-keysyms1 (>= 0.3.6) but it is not installable
       Depends: libxcb-randr0 (>= 1.1) but it is not installable
       Depends: libxcb-xv0 (>= 1.2) but it is not installable
       Recommends: vlc-plugin-notify (= 1.1.4-1ubuntu1.4) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 1.1.4-1ubuntu1.4) but it is not going to be installed
E: Broken packagesI get similar errors in synaptic package manager too. I sense that something is wrong with the repositiory etc. I have had no success with other packages also - googleearth, nmap , gimp , etc.
Could someone help me out with this.
thanks in advance
nishith

---

### Post by philinux on 2011-03-19
nkdnkd,

Try running this to fix broken packages. You can also do this from within synaptic. Post back any errors.

Which ubuntu version have you installed,

```
sudo apt-get install -f
```

---

### Post by nkdnkd on 2011-03-19
thanks a ton
I tried and I am already through with installing zenmap and gimp. 
I shall try out vlc too. It is presently taking a lot of time and getting timed out in between. Must be a problem with the internet connection.
thanks again
regards
nkd

---

### Post by oldos2er on 2011-03-19
Have you run ```
sudo apt-get update
``` lately?

---

### Post by nkdnkd on 2011-03-19
hi phil,
I tried out vlc installation a couple of times, but without any avail. The result was always as under :-
> nishith@nishith-Aspire-4720:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libaudio2 libcddb2 libdvbpsi6 libebml2 libiso9660-7 libmatroska2 libqt4-dbus
  libqt4-xml libqtcore4 libqtgui4 libsdl-image1.2 libtar libupnp3 libva-x11-1
  libvcdinfo0 libvlc5 libvlccore4 libx264-98 libxcb-keysyms1 libxcb-randr0
  libxcb-xv0 vlc-data vlc-nox vlc-plugin-notify vlc-plugin-pulse
Suggested packages:
  nas qt4-qtconfig mozilla-plugin-vlc videolan-doc
The following NEW packages will be installed:
  libaudio2 libcddb2 libdvbpsi6 libebml2 libiso9660-7 libmatroska2 libqt4-dbus
  libqt4-xml libqtcore4 libqtgui4 libsdl-image1.2 libtar libupnp3 libva-x11-1
  libvcdinfo0 libvlc5 libvlccore4 libx264-98 libxcb-keysyms1 libxcb-randr0
  libxcb-xv0 vlc vlc-data vlc-nox vlc-plugin-notify vlc-plugin-pulse
0 upgraded, 26 newly installed, 0 to remove and 287 not upgraded.
Need to get 641kB/21.3MB of archives.
After this operation, 63.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main libxcb-randr0 i386 1.6-1 [16.1kB]
Get:2 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main libxcb-xv0 i386 1.6-1 [12.9kB]
Get:3 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/universe libupnp3 i386 1:1.6.6-5 [123kB]
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/universe libx264-98 i386 2:0.98.1653+git88b90d9-3ubuntu2
  Could not connect to in.archive.ubuntu.com:80 (111.91.91.37). - connect (110: Connection timed out)
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main libxcb-keysyms1 i386 0.3.6-1build1
  Unable to connect to in.archive.ubuntu.com:http:
Fetched 152kB in 1min 6s (2,271B/s)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/x/x264/libx264-98_0.98.1653+git88b90d9-3ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/x/x264/libx264-98_0.98.1653+git88b90d9-3ubuntu2_i386.deb)  Could not connect to in.archive.ubuntu.com:80 (111.91.91.37). - connect (110: Connection timed out)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/x/xcb-util/libxcb-keysyms1_0.3.6-1build1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/x/xcb-util/libxcb-keysyms1_0.3.6-1build1_i386.deb)  Unable to connect to in.archive.ubuntu.com:http:
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

I have done apt-get update and it didnot help.
What could be the problem ?!?
thanks in advance
nkd

---

### Post by CharlesA on 2011-03-19
Change which mirror you are using by going to software sources.

---

### Post by NJPinator on 2011-03-19
The first thing I'd suggest is do it the "Absolute Beginner" way and install GIMP, VLC and the like via the Ubuntu Software Center. As for packages like Google Earth, they're not in the default repositories (you'll just get a ton of community-based crap -- no offence people, I like it official :D).

If that doesn't work, all the "-f" switch does is force installation; the error messages you're getting note that you don't have specific versions of packages installed -- I assume you at least know what dependencies are, being a former Fedora user. However, me and the kernel aren't great friends, so I, personally, would re-install Ubuntu in it's entirety.

P.S. My advice is advice, not mandatory. Re-installing Ubuntu would be a worst case scenario.

---

### Post by nkdnkd on 2011-03-19
thanks guys,
I could finally work out the vlc problem. Nothing specific but I first finished installing the gstreamer plugins - ffmpeg, bad and ugly ones. Thereafter the vlc installation worked like a charm. 
My guess there might have been some common dependencies - the lib*.* files which got installed with the gstreamer stuffs.
Anyway, Next shall be the googleearth. 
BTW, I have installed ubuntu on a usb drive (8GB). A situation may arise when there would be a need to reinstall ubuntu in future. But in that case I wish to save the trouble to downloading all these add on software again from the internet. In fedora yum allows to keep the downloaded rpms and the dependencies in a local repository on the hdd, so that takes care of future reinstalls. I wish to keep the installers alongwith the resolved dependencies on my hdd.
Pls advise and thanks in advance for all the support 
nkd

---

### Post by oldos2er on 2011-03-20
Ubuntu stores installed packages in /var/cache/apt/archives

---

### Post by nkdnkd on 2011-03-21
hi oldos2er,
I found he .deb files in the /var/cache/apt/archives folder.
Now how to proceed with these when I wish to set up the particular application / software on a different ubuntu machine, which doesnot have the internet access. Do I simply copy these files to the machine and execute
> dpkg -i name_of_software
thanks for all the help
regards 
nkd

---

### Post by CharlesA on 2011-03-21
Just copy them to /var/cache/apt/archives and then apt-get install whatever package you were going to install.

---

### Post by NJPinator on 2011-03-26
CharlesA's method would work, but you could alternatively use the dpkg command as you said yourself.

Put the Debian installers wherever you like, then execute:
```
dpkg -i <deb file location>
```

For example:
```
dpkg -i /home/myuser/Downloads/installer.deb
```

As simple as it is...hope that helps!

---

### Post by nkdnkd on 2011-03-30
> Put the Debian installers wherever you like, then execute:
 	Code:
 	dpkg -i <deb file location>


And I suppose that the dependencies would have to be resolved manually ?!?!
is that right ?
regards
nishith

---

### Post by CharlesA on 2011-03-30
> **nkdnkd said:**
> And I suppose that the dependencies would have to be resolved manually ?!?!
is that right ?
regards
nishith
A simple:

```
sudo apt-get install -f
```

Would fix that.

---

### Post by nkdnkd on 2011-03-31
thanks a lot for the help
I will try that out.
regards
nishith

---

### Post by NJPinator on 2011-03-31
> **nkdnkd said:**
> And I suppose that the dependencies would have to be resolved manually ?!?!
is that right ?
regards
nishith

Personally, I'd open the Debian Installer in GDebi, using...

```
gdebi-gtk <deb file location>
```

...which states whether the file is compatible with your hardware and automatically resolves dependency issues. As a little side function, it also displays all included archive files, in case you want to extract them (e.g. if a dependency wasn't installed correctly, you could extract the source code and re-compile it for your specific architecture -- like i386 -- but that's a little much!)

And I think you should note that...

> **CharlesA said:**
> A simple:

```
sudo apt-get install -f
```

Would fix that.

...is only possible if your *.deb file(s) are in the **/var/cahce/apt/archives** directory, as **CharlesA** had already stated in post #11:

> **CharlesA said:**
> Just copy them to /var/cache/apt/archives and then *apt-get install* whatever package you were going to install.

Also, forcing installation using the 'f' switch can lead to a program not functioning correctly as it ignores the need for dependencies. Most of the time, you should only force installation of a package if nothing else works (but that's just my advice).

---

### Post by CharlesA on 2011-03-31
> **NJPinator said:**
> 
...is only possible if your *.deb file(s) are in the **/var/cahce/apt/archives** directory, as **CharlesA** had already stated in post #11:

It will download packages as needed. If the machine doesn't have an internet connection, you'd have to download the dependencies with something like aptoncd and put them in /var/cache/apt/archives/

> Also, forcing installation using the 'f' switch can lead to a program not functioning correctly as it ignores the need for dependencies. Most of the time, you should only force installation of a package if nothing else works (but that's just my advice).

-f isn't "force"

> -f
--fix-broken
    Fix; attempt to correct a system with broken dependencies in place. This option, when used with install/remove, can omit any packages to permit APT to deduce a likely solution. Any Package that are specified must completely correct the problem. The option is sometimes necessary when running APT for the first time; APT itself does not allow broken package dependencies to exist on a system. It is possible that a system's dependency structure can be so corrupt as to require manual intervention (which usually means using dselect(8) or dpkg --remove to eliminate some of the offending packages). Use of this option together with -m may produce an error in some situations. Configuration Item: APT::Get::Fix-Broken. 

[http://linux.die.net/man/8/apt-get](http://linux.die.net/man/8/apt-get)

---

### Post by NJPinator on 2011-04-01
> **CharlesA said:**
> It will download packages as needed. If the machine doesn't have an internet connection, you'd have to download the dependencies with something like aptoncd and put them in /var/cache/apt/archives/



-f isn't "force"



[http://linux.die.net/man/8/apt-get](http://linux.die.net/man/8/apt-get)

Damn, I'm stupid sometimes. :( Ironic enough that it's the exact opposite of what I made it out to be... :D

---

### Post by CharlesA on 2011-04-01
> **NJPinator said:**
> Damn, I'm stupid sometimes. :( Ironic enough that it's the exact opposite of what I made it out to be... :D
Not stupid, no one knows everything. ;)

---

### Post by nkdnkd on 2011-04-02
thanks a lot for all the help you all have extended and a bit of googling about has helped me create my own offline repo on the hard disk.
The following steps did the trick :-
> # 1. make a dir accessible (atleast by root)
          
          sudo mkdir /var/my-local-repo

# 2. copy all the deb files to this directory.

# 3. cd to the /var/my-local-repo directory and  run the following command to create the
     Packages.gz file that is needed to for Synaptic to “see” your repository:

          sudo dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz

    # Please note that every time you add any more .deb files to this folder, you have to create a
      new Packages.gz file using the above command before the new file(s) will show up in Synaptic
      (or Aptitude).

    # Be sure to install the build-essential package (sudo apt-get install build-essential) before
      running the above command.

# 4. Edit the /etc/apt/sources.list file and insert this on a new line (preferably the first):

          deb file:/var/my-local-repo/ /

    # the forward slash at end is not a typo and also note the single space between the last two 
    slashes.

# 5. Reload the package index like this:

          sudo apt-get update

# 6. Now open System->Administration->synaptic package manager and do the following :-
      Settings->Repositories-> Deselect every repo other than the file:/var/my-local-repo under
      the Ubuntu Software and Other Software tabs.

          Click the reload button.

# 7. To install your favourite software from the local repo just do :-
          
          sudo apt-get install <softwareName>
Hope that helps all the newbies like me.
thanks again
nishith

---

