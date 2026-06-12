---
title: "Auto mount drive syntax question"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by luke0927 on 2009-11-09
Ok i used pysdm to edit fstab to auto mount my windows drive....below is the entry....since im still a newbie just wanting to understand what the part after the file system type means...basically what is this telling the system.  Thanks!

"nls=iso8859-1,ro,umask=000  0  0"

/dev/sdb1                                  /media/sdb1     ntfs         nls=iso8859-1,ro,umask=000  0  0

---

### Post by Steve Roscio on 2009-11-09
The part after the filesystem name (the options) depends upon the filesystem.  Many options are filesystem-independent, but some are only for the specific filesystem.   In your case, it's ntfs.  The man page for [FONT=Courier New][COLOR=DarkRed]mount[/COLOR][/FONT] explains the options.  I won't post the filesystem independent ones (there's too many), but here's the ones for ntfs:

Mount options for ntfs
       iocharset=name
              Character set to use when returning file  names.   Unlike  VFAT,
              NTFS  suppresses  names  that  contain unconvertible characters.
              Deprecated.

       nls=name
              New name for the option earlier called iocharset.

       utf8   Use UTF-8 for converting file names.

       uni_xlate=[0|1|2]
              For 0 (or `no' or `false'), do  not  use  escape  sequences  for
              unknown  Unicode  characters.   For 1 (or `yes' or `true') or 2,
              use vfat-style 4-byte escape sequences starting with ":". Here 2
              give  a  little-endian  encoding  and  1 a byteswapped bigendian
              encoding.

       posix=[0|1]
              If enabled (posix=1),  the  file  system  distinguishes  between
              upper  and lower case. The 8.3 alias names are presented as hard
              links instead of being suppressed. This option is obsolete.

       uid=value, gid=value and umask=value
              Set the file permission on the filesystem.  The umask  value  is
              given in octal.  By default, the files are owned by root and not
              readable by somebody else.

---

### Post by luke0927 on 2009-11-09
Thanks Steve

---

### Post by luke0927 on 2009-11-13
Anyone have any idea why the drive is mounting in read only?  I have to unmount the drive and then remount it to have read/write to it?

edit i found the problem in pysdm it is defaulted to read only when it mounts...can you tell that from the entry in /etc/fstab?

---

