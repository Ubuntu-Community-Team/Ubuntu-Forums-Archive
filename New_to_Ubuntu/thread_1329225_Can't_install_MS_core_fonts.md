---
title: "Can't install MS core fonts"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by quinnten83 on 2009-11-17
i can't install the MS corefonts.
I keep getting an error about sourceforge not resolving.
I know sourceforge was about to change their name, could that be causing this?
If that is the case, what will the developers do about this, a lot of .debs on the repos refer to sourceforge.

```
E: ttf-mscorefonts-installer: subprocess installed post-installation script returned error exit status 1
```

```

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2009-11-17 12:59:13--  http://downloads.sourceforge.net/corefonts/andale32.exe
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-11-17 12:59:23--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `switch.dl.sourceforge.net'
--2009-11-17 12:59:33--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving mesh.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `mesh.dl.sourceforge.net'
--2009-11-17 12:59:43--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving dfn.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `dfn.dl.sourceforge.net'
--2009-11-17 12:59:53--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving heanet.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `heanet.dl.sourceforge.net'
--2009-11-17 13:00:03--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving jaist.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `jaist.dl.sourceforge.net'
--2009-11-17 13:00:13--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving nchc.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `nchc.dl.sourceforge.net'
--2009-11-17 13:00:23--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving ufpr.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `ufpr.dl.sourceforge.net'
--2009-11-17 13:00:33--  http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internode.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `internode.dl.sourceforge.net'
--2009-11-17 13:00:43--  http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving voxel.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `voxel.dl.sourceforge.net'
--2009-11-17 13:00:53--  http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving kent.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `kent.dl.sourceforge.net'
--2009-11-17 13:01:03--  http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internap.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `internap.dl.sourceforge.net'
sha256sum: andale32.exe: No such file or directory
andale32.exe: FAILED open or read
sha256sum: WARNING: 1 of 1 listed file could not be read
Checksum mismatch for andale32.exe, aborting!
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mscorefonts-installer
```

---

### Post by philinux on 2009-11-17
[https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217](https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217)

See post #21 for fix.

Seems to affect wireless connections more than wired.

---

### Post by atomizer on 2009-11-17
I have uninstalled and reinstalled MS-corefonts and I have no problem with sourceforge.

I have ubuntu 9.10.

Maybe the server was down for a moment?

---

### Post by Golem XIV on 2009-11-17
> **philinux said:**
> [https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217](https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217)

See post #21 for fix.

Seems to affect wireless connections more than wired.

The solution you point to will only patch over this specific symptom of a more pervasive problem that Ubuntu has - the lack of a local, persistent DNS cache.  This is why wget times out in the first place.

If you want to fix the underlying problem, I recommend that you follow the instructions posted [here]("http://ubuntuforums.org/showpost.php?p=7902019&postcount=33").

I have been using variations of this procedure on all my Ubuntu installs since Gutsy and it really makes a difference.  It will also solve the problem of font installations.

---

### Post by quinnten83 on 2009-11-18
I got this problem when I was installing in a virtual machine on my work laptop.
I had already installed Ubuntu 9.10 on a USB stick to try it out, but an update borked that installation. So I decided to reinstall yesterday and again with the mst-corefonts problems. This is becoming a bit persistent.
Don't get me wrong, I am not trying to be ungrateful to the community that provided me a top notch OS for zip, but I feel like we are falling behind because of these little paper-cuts. Yes, I do not need to install the darn corefonts, but if it is an option, I would kinda like it to work. And how is it that it fails on some computers and not on others, where is the error coming from? I didn't have this with my first install of Karmic.
I haven't tried the solutions yet, I will later when I upgrade my Desktop to karmic, but I am already slightly frustrated. Karmic was to me the beesknees, looked good (once you chose the dust theme) and seem to perform admirably, but a few little niggles, amongst others this corefont thing is ruining my fun.

---

### Post by quinnten83 on 2009-11-22
The solution did work!
However, I'm thinking that this might be related to the default use of IPv6 in Ubuntu. MY websurfing is also quite slow. I turned IPv6 off in Firefox on my desktop and now it's back to it's old speed. everything else that uses an internet connections remains slow as molasses.
I am pretty sure that my router can't handle IPv6.

---

