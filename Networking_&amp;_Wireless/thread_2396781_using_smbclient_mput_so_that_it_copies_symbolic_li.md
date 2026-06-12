---
title: "using smbclient mput so that it copies symbolic link (not the target of link)"
date: 2018-07-20
forum: Networking &amp; Wireless
---

### Post by jmartin-wustl on 2018-07-20
Is there a way I can run mput under smbclient in such a way that it just copies the symbolic link itself rather than copying in the full target of the symbolic link?  

I guess another question I have would be if there is a way to have smbclient's mput to resume on failure?   I am trying to recursively move some large directories (500Gb+) and I am getting frequent premature stops.  Would be very useful if I could just pick up where I left off

Thanks,
John

---

### Post by TheFu on 2018-07-21
Welcome to the forums.

I don't know much about CIFS, but you can tell **rsync** to treat symbolic links as symbolic links.
rsync has  multiple options so that almost any required way symbolic links need to be handled, can.
From the manpage:
```
       --copy-unsafe-links
              This  tells  rsync  to  copy the referent of symbolic links that
              point outside the  copied  tree.   Absolute  symlinks  are  also
              treated  like  ordinary  files,  and  so are any symlinks in the
              source path itself when --relative is used.  This option has  no
              additional effect if --copy-links was also specified.

       --safe-links
              This  tells  rsync to ignore any symbolic links which point outâ
              side the copied tree. All absolute symlinks  are  also  ignored.
              Using  this option in conjunction with --relative may give unexâ
              pected results.

       --munge-links
              This option tells rsync  to  (1)  modify  all  symlinks  on  the
              receiving side in a way that makes them unusable but recoverable
              (see below), or (2) to unmunge symlinks on the sending side that
              had  been stored in a munged state.  This is useful if you donât
              quite trust the source of the data to not try to slip in a  symâ
              link to a unexpected place.
...
SYMBOLIC LINKS
       Three  basic  behaviors  are  possible when rsync encounters a symbolic
       link in the source directory.

       By default, symbolic links are  not  transferred  at  all.   A  message
       "skipping non-regular" file is emitted for any symlinks that exist.

       If --links is specified, then symlinks are recreated with the same tarâ
       get on the destination.  Note that --archive implies --links.

       If --copy-links is specified, then symlinks are "collapsed" by  copying
       their referent, rather than the symlink.
....
```
Lots more on links in the manpage.

So I looked briefly at the smbclient manpage. There's mention of a 'tar' capability. Tar has many options around symlinks. If you must use smbclient (eewwwww), then that might be the only way.

rsync is a much better tool for what you've described you need.   rsync is in my top 5 for computer related inventions, just after Unix and ssh.

---

### Post by jmartin-wustl on 2018-07-25
Yeah, unfortunately my only option to connect to this particular volume is smbclient (I agree ... ewww).   I'll look a bit more into tar mode and see if I can figure something out.  Thanks

---

### Post by SeijiSensei on 2018-07-26
CIFS has no support for POSIX symlinks.  Windows uses "shortcuts," but they are not the same as symlinks.

rsync cannot help with this issue.  If you use rsync with a Windows-formatted target, you will lose permissions and symlinks.  

Rather than use smbclient, have you tried [mounting the Windows filesystem into the Linux directory tree]("https://wiki.ubuntu.com/MountWindowsSharesPermanently")? Then you can use regular tools like cp and tar to copy files and clone filesystems.  You still won't be able to transfer symlinks though.

---

### Post by jmartin-wustl on 2018-07-26
The volume I'm trying to reach was setup by my university and there are 2 approved ways to reach it, one being NFS mount and the other using smbclient.  Unfortunately my workstation (for which I am not an admin) for some reason doesn't support the NFS solution which I would have much preferred, leaving me with smbclient.   In fact just to use smbclient I'm having to run a docker container running a newer version of ubuntu that supports smblient -m SMB3.   Hmm, I wonder if I could setup a container that would enable me to just mount the filesystem as you suggest.  I'll look into it.  I'm a novice at all this docker stuff but so far I've been able to stumble through.  Thanks!

---

### Post by TheFu on 2018-07-26
It sounds like the other system isn't Windows. 

Could you use a software-based VM like qemu  (not KVM) and run a light Linux with read-only NFS client inside it?   They you can use rsync and maintain symlinks.

---

