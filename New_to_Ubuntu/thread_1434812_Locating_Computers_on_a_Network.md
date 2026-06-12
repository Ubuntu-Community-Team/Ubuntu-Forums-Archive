---
title: "Locating Computers on a Network"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by Beraid on 2010-03-20
I have another computer on the network running Windows Vista set up for file sharing. All my stuff was backed up to a file on there. How do I access that computer/file? In Ubuntu it would list it in the Network folder but in Xubuntu I don't even know where the Network folder is located. When I click Places it's not listed in there.

Any ideas?

---

### Post by Cinnander on 2010-03-20
Hi, you can use Gigolo to browse the shares from windows machines; it's located under Applications > System as "Remote Filesystems". You can see the network structure if you turn on the Side Panel (under the View menu).

For some reason a couple of rather critical packages that let you actually use Gigolo to open SMB shares with Thunar are not installed by default; you can follow [the instructions here](http://www.uvena.de/gigolo/help.html#open-resources-in-thunar-on-xfce-4-4-and-4-6) ("Open resources in Thunar on Xfce 4.4 and 4.6") to take care of the missing packages and configuration. Note the need to log out and in again after completing these steps.
Once you've done this you'll be able to mount shares under ~/.gvfs/ somewhere just by opening them with Gigolo.

An alternative method used with older versions of Xubuntu was to use the fuse-smb package to 'mount' all SMB shares as they were discovered at a specific location (e.g. /smb), which allows you to browse it akin to 'My Network Places'; instructions for that method are [along these lines](http://ubuntuforums.org/showthread.php?t=304131), though probably somewhat out of date by now. The shares would all be mounted as a particular user from the fuse group (which you would add yourself to) so for a single user system /smb is fine but otherwise you would probably want to use a mountpoint in your home folder. An additional inconvenience is being unable to specify usernames/passwords for shares without using a text editor.

---

