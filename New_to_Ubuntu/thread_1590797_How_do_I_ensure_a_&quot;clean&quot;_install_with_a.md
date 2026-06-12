---
title: "How do I ensure a &quot;clean&quot; install with a separate /home partition"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by laptoplinux on 2010-10-08
When 10.10 releases, I plan to upgrade as soon as possible.  I have a separate /home partition, so I'm just going to install from a disc and then reinstall my applications.  

But how can I make sure that the install is completely clean while preserving all of my data?  In other words, I want to make sure that there aren't any dot files or other hidden preference folders carried over from my current 10.04 install while preserving all of my files.  A clean slate as far as application preferences and system configuration goes, but with all my user data intact.  At the same time, I don't want to overzealously delete a hidden folder or file in my /home dir that I should probably leave alone.

---

### Post by cek on 2010-10-08
In most cases, people suggest a seperate /home partition so that you can maintain your data and preferences between installations.

Since you only want to retain your data, this becomes a little more tricky.  Basically, there is no simple way to purge only configuration files from your home folder, because potentially you could put data "anywhere".

I encountered this same problem when I first started playing around with linux in about 1999.  What I've done that has worked very well for me is the following partitioning scheme.

/boot  -- small, ~256MB, only really need kernel images and grub
/      -- medium, ~64GB, root fs never really takes up more than ~12GB, leaving lots of room for logs and temp space
/swap  -- 2GB
/home  -- 16GB -- this is ONLY for preferences and things that get installed to /home (like wine, etc.)
/data  -- the rest -- this is a huge partition that I keep all my data files on.

Using this scheme, I can reinstall cleanly and elect to keep my data and preferences (keeping the /home and /data mount points), or just my data.

In your case, you need to identify any files that you want to keep that exist in hidden (./.*) files/directories, and ensure they have been backed up along with all your other files you wish to keep.  Then remove all your hidden files/directories in your home folder.  I've not posted the commands to do this (I'm sure you know them already), because there is inherent risk with removing portions of the directory structure -- I don't know where you've kept your files or if anything important is in a hidden directory...

Safest thing would be to backup your entire /home folder to an external drive, then reinstall (cleanly), then bring your files back in.  If you go that route, I suggest adding a separate partition (like described above) to make this easier in the future.

---

### Post by laptoplinux on 2010-10-08
Thanks for the reply.  I usually just to an in-place upgrade from one Ubuntu to the next, but every so often I like to do a clean slate install, maybe after 4 releases or so.  I know it isn't needed, but I've found that, as time goes on and applications grow and change, occasionally a preference file left over from several releases ago can result in minor odd things here and there.  Not necessarily bad, just sub-optimal.  And that only happens when I've been doing an inordinate amount of screwing around with my system, which I have been lately.

---

### Post by Locke_99GS on 2010-10-08
I've never had a problem removing *. files and folders from my /home partition, followed by installing over the / partition. Granted now, I have no idea what kind of data may be contained in YOUR hidden folders, but for me I lost nothing I cared about. (all Docs, Downloads, Videos, Pictures, etc... remained)

---

### Post by QLee on 2010-10-08
[QUOTE=laptoplinux]Thanks for the reply.  I usually just to an in-place upgrade from one Ubuntu to the next, but every so often I like to do a clean slate install, maybe after 4 releases or so.  I know it isn't needed, but I've found that, as time goes on and applications grow and change, occasionally a preference file left over from several releases ago can result in minor odd things here and there.  Not necessarily bad, just sub-optimal.  And that only happens when I've been doing an inordinate amount of screwing around with my system, which I have been lately.[/QUOTE]
I'm stating this in generalities because we don't have something specific to discuss but I generally find that when upgrading packages I am given a choice to keep my altered configuration or accept the package maintainers new version. It seems to me that if you always chose to accept the new version, you would get a "clean" system (but you might also lose some package configuration you want). In this situation, I sometimes have to pause upgrading while I investigate whatever changes are coming with the new configuration proposed. It can be a lot of work but you may consider it worth the effort. You'll always have your ~home backup to consult or refer to if you need to get back to an old configuration.

I'm not sure upgrading as soon as possible is the best advice, YMMV, but it's your choice to make. You'd be well advised to run the live CD (or USB) on your system to test it before trying the upgrade but I expect you know that. My in-place upgrades have worked too, but lots of people seem to report failure, I'm not sure that all of them read and understand the release and upgrade notes for a new release before starting.

Good luck!

---

### Post by Megaptera on 2010-10-08
Useful partitioning guide with screenshots for 10.04 so it'll work for 10.10 I expect

[http://www.linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/2/](http://www.linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/2/)

---

### Post by da burger on 2010-10-08
Personally I would suggest that if you want to keep files but not data then you should just take a tarball of all your file folders, do a complete fresh reinstall, then recover that tarball into your home dir.
Hope that helps
Angus

---

