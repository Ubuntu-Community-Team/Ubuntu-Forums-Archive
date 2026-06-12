---
title: "SCP to windows problem"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by Gluebuntu on 2011-02-22
I have a problem with using SCP from my linux box to a windows machine on my network.

On my windows machine, I have game files that I need to transfer to my Linux box every day. I've found scripts on the internet to help me do this automatically, but I can't get the SCP command right, it always gives me an error. I have freeSSHd setup on the windows machine and I am able to login but the SCP command always fails.

My command is:

```
scp <windows user name>@192.168.1.102:C:\WINDOWS\<some file> /home/<linux user name>/<some folder>
```

After I put in my password it either complains about file name (I think) or it says:

```
exec request failed on channel 0
lost connection

```

I know people have had this sort of question loads of times before but I couldn't find any instructions specific to my problem by googleing.

Is it anything to do with windows using backslash and Linux using forward slash for path names?

Please help me find the right scp command, manually sftp-ing is very annoying :(

More info:

My Linux box is running Ubuntu 10.04

My windows machine is using Windows XP

This is on the same network.

I have the firewall setup properly on both computers.

---

### Post by The Cog on 2011-02-22
You almost certainly need to put single-quotes round the source file name in order to keep the backslashes.

I'm dubious about the C: too - I know that cygwin uses something like /cygwin/c/filename instead of c:/filename but I can't remember the exact format, and I don't know if freeSSHd is the same anyway. Do it might be worth just doing it without the C: like this:
 > scp '<windows user name>@192.168.1.102:\WINDOWS\<some file>' /home/<linux user name>/<some folder>

---

