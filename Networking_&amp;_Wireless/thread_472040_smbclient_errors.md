---
title: "smbclient errors"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by prezbedard on 2007-06-12
I've run into a stange issue when using smbclient to move files to/from a 2003 server to fiesty.


When I run a command either put or get on a file in the local linux diractory that I was last in before invoking smbclient it works fine.

So say I was in my home dir and I use smbclient in //server/share

 if test.txt is in my home dir 

put test.txt works

however if I go into smbclient and run

put /tmp/test.txt I get

NT_STATUS_OBJECT_NAME_INVALID opening remote file

This only happens when referring to a file outside of the last linux dir I was in.

any ideas?

Thanks,

---

### Post by prezbedard on 2007-06-18
found the problem

it is necessary to use 

smb:\> lcd /newlocaldir

to change from the cureent working local director to the one you want

from samba.org

> Notice how the prompt changes to reflect the new current working directory. To change your current directory on the local system, use the lcd command:

    smb: \trans\> lcd /u/snd
    the local directory is now /u/snd

---

