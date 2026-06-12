---
title: "[SOLVED] Xfce, thunar, and samba shares"
date: 2008-03-18
forum: Networking &amp; Wireless
---

### Post by snorkytheweasel on 2008-03-18
For openers - I should be able to see, write, and read the samba shares in my Windows domain. My Ubuntu and Kubuntu computers do this simply and flawlessly using Dolphin. All of the *buntu machines have joined the domain and appear in Active Directory. I can ping to and from the *buntus & windows computers- using host name and/or IP address.

Using Xubuntu with Xfce and Thunar (I think that's Viking for 'braindead') I cannot find those same shares and I am baffled by how to find and mount those shares.

Dolphin won't run on my Xfce setup, and I can't find a GUI-based File Manager - except Thunar - that *will* run in it.

Yes, I have LinNeighborhood installed on the Xubuntu/Xfce system. It hasn't made any difference.

I've attempted the techniques from previous threads - techniques that have me exhausted from jumping through hoops. I don't consider myself to be a GUI cripple (25 years  working with DOS, Windows command, VMS and *NIX), but Thunar is just a ridiculous waste of time. Besides, my boss IS a GUI cripple and he needs something simple to use when he can't find me :lolflag: :lolflag:

The questions:
[LIST=1]
[*]Rhetorically asking, why isn't there a simple Xfce equivalent to the elegant solutions in Gnome and KDE?
[*]How do I use Xfce or another lighter-than Gnome/KDE to simply and effortlessly work with my Samba shares?
[*]Am I expecting too much?
[/LIST]

</whine>

---

### Post by Eiríkr on 2008-03-18
FWIW, Konqueror runs just fine on my Xubuntu Gutsy machine, after installing via Synaptic / apt-get (to make sure all the various dependencies get pulled down too).  Thunar meanwhile is **only** a file manager -- it has none of the network ioslave goodness that comes with Konqueror.  (For that matter, Nautilus is pretty sparse too -- it can't see any zeroconf services or browse NFS shares, whereas Konq can.)

So to answer your specific questions:
[list=1][*]XFCE is deliberately pared down.  It is meant to be a bare-bones, and therefore lightweight, GUI for situations that require less GUIness and might possibly only be able to handle a lighter-weight GUI framework.  If this means that the proverbial kitchen sink isn't included in the file browser, so be it.  Thunar is meant to be a file browser.  It browses files.  Not network shares.

[*]Get at least slightly used to the command line.  You'll need to manually mount the Samba shares to your local filesystem, and **then** you can use Thunar to browse those files to your heart's content.  Create a new and empty directory for the share, say [font=courier]/share[/font], then mount the Samba share there.
```
sudo mkdir /shares
sudo mount.cifs //SAMBA_SERVER/SHARE /share -o username=USERNAME,rw
```
Have a look at [font=courier]man mount.cifs[/font] for all sorts of fun options to include after the [font=courier]-o[/font] flag.  Try experimenting with them until you get what you need.  Useful ones to try are [font=courier]uid[/font] and [font=courier]gid[/font] to define who gets ownership of the mounted share (otherwise it defaults to root).  

Unfortunately, it sounds like there are problems with how Ubuntu boots that prevents Samba shares from being automounted at boot time.  However, adding the Samba share(s) to the [font=courier]/etc/fstab[/font] file and allowing users to mount / unmount would make it possible to create short mounting scripts for users that would run on login instead of boot.  

[*]No.  ;)  But you might need to rethink your assumptions / approach (c.f. 2. above).  [/list]

Cheers,

Eiríkr

---

### Post by snorkytheweasel on 2008-03-18
> **Eiríkr said:**
> FWIW, Konqueror runs just fine on my Xubuntu Gutsy machine, after installing via Synaptic / apt-get (to make sure all the various dependencies get pulled down too). 

I installed Konqueror:
apt-get update
apt-get install konqueror
The Konqueror installation appeared to complete successfully. However, there are three conditions worthy of note:
[LIST=1]
[*]In the applications menu, a new tool appeared: "Settings". It has a long list of options that will help accomplish tasks that I thought I'd have to perform by manually tweaking configuration files.  Why it didn't show up until I installed Konqueror sounds like a question for the sages through the ages.
[*]Also in the applications menu, Konqueror did NOT appear. It joins a short list of GUI-based programs that are installed but are not in the applications menu (e.g., there are 3 terminal emulators that are installed but 2 of those don't show up in the apps menu). Attempting to run these programs from the command line generates an error:
Cannot connect to X server. 
[*]Dolphin woke up and does exactly what I want it to do: it seamlessly and effortlessly finds my samba shares. It does that without my having to mount the share. As a bonus,  it does everything that Thunar does.
[/LIST]
It would be nice to get konqueror (and some of his friends) to come out of hiding and join the GUI crowd. For the moment, however, I'm content. I might start a new thread to discuss the programs that aren't listed in the application menu.

Thanks for your help. Life got a lot better when I could work with files over in the windows neighborhood.

Now Thunar can go get the nap it so badly needs. :wink:

---

### Post by Eiríkr on 2008-03-19
Glad to help out.  :)  

I'm confused that your Settings menu was missing; sounds like maybe a hiccup in XFCE.  The menu on my install was there after the 7.10 install (can't remember specifically anymore what 7.04 included).  That said, Konq is indeed missing from the GUI apps menu for me too.  I think it's because KDE apps might not integrate too well with XFCE; I recall when similar problems cropped up for KDE apps in Gnome or vice versa, and it took a good bit of coordination and effort from both the KDE and Gnome dev communities to get them to cooperate better.  FWIW, you can still launch Konq from the CLI, and I imagine it'd be easy enough to add Konq to the menu (though I admittedly haven't bothered yet; but then I just use Konq for bug-hunting on the boards here :)).  

Anyway, glad things are working for you.  :D

Cheers,

Eiríkr

---

### Post by foresto on 2008-06-25
Alternatively, you might want to try the smbnetfs or fusesmb packages.  They will make your windows network shares appear as directories in your filesystem, which you can browse and manipulate with Thunar or any other tool.

I had to:
1. Install smbnetfs.
2. Create a directory to contain network shares.
3. Run "smbnetfs /path/to/directory".

To get it working automatically whenever I log in, I just had to turn step 3 into an autostarted application (which you can do from the XFCE Settings Manager).

To get it to work with password-protected network shares, I had to RTFM and put my credentials in the appropriate config files.

---

