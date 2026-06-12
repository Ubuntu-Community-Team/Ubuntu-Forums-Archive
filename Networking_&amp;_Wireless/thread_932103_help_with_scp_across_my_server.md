---
title: "help with scp across my server"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by engineer85 on 2008-09-28
I am having trouble using "scp"  I type this into my terminal window, and get an error, however, if I go to Places>Connect to Server, and then key in the username and hostname of the comp I wish to sftp to, I am able to copy files between my local computer and the remote one.  (Actually it is not remote, just a computer in a different room which I am networked to).

```
controls@UTAEngineer:/$ sudo scp controls@UTAEngineer:/home/controls/WINDOWS_FILES mokrunka@Engineer:/WINDOWS_FILES
controls@utaengineer's password: 
Permission denied, please try again.
Permission denied, please try again.
Permission denied (publickey,password).
lost connection
```

Any suggestions?

---

### Post by engineer85 on 2008-09-28
Is this post in the correct area?  Any help?

Thanks,

Steve

---

### Post by digitalvectorz on 2008-09-28
Steve,

Are you trying to copy files from your local machine (UTAEngineer) to (mokrunka@Engineer)?

Just a suggestion (I'm not able to recreate that problem at the moment), but try this:

```

controls@UTAEngineer:/$ sudo scp /home/controls/WINDOWS_FILES mokrunka@Engineer:/WINDOWS_FILES

```

i'm not completely sure.  What's throwing me off is why it's asking for the password for controls@UTAEngineer if that's the machine your on and not asking for mokrunka@Engineer (since that appears to be the remote host).

---

### Post by engineer85 on 2008-09-28
> **digitalvectorz said:**
> Steve,

Are you trying to copy files from your local machine (UTAEngineer) to (mokrunka@Engineer)?

Just a suggestion (I'm not able to recreate that problem at the moment), but try this:

```

controls@UTAEngineer:/$ sudo scp /home/controls/WINDOWS_FILES mokrunka@Engineer:/WINDOWS_FILES

```

i'm not completely sure.  What's throwing me off is why it's asking for the password for controls@UTAEngineer if that's the machine your on and not asking for mokrunka@Engineer (since that appears to be the remote host).

Digital, thanks for the response.  I'm also confused.  I ran the code per your suggestion, but got the same issue.  The reason I ran it the way I did was from this man page:

SYNOPSIS
     scp [-1246BCpqrv] [-c cipher] [-F ssh_config] [-i identity_file]
         [-l limit] [-o ssh_option] [-P port] [-S program]
         [[user@]host1:]file1 ... [[user@]host2:]file2

I guess it works the same either way though.  It is strange that I can use the GUI sftp from the "Places" menu, and the file x-fer works fine, but not through scp...  I should have given more info though, sorry.  The local machine (UTAENgineer) is where the WINDOWS_FILES directory is, and the "remote" machine (but on the same network, just a diff. room) is Engineer, which is where I am trying to copy the files to (and in fact successfully did with sftp through the GUI).

Thanks again,

Steve

---

### Post by digitalvectorz on 2008-09-29
> 
I guess it works the same either way though. 


Actually, it doesn't work the same either way.  It actually (from my tests on it) runs like this.
```

scp host1:/file/to/be/copied host2:/where/to/copy/file/to

```

If you reverse the order (with two different hosts), like this:
```

scp host2:/where/to/copy/file/to host1:/file/to/be/copied

```
It will copy /where/to/copy/file/to over top of /file/to/be/copied (if it exists) 
-OR=
It will balk and tell you that /where/to/copy/file/to does not exist.


**->** Can you SSH to localhost?
(SCP uses SSH protocol, so it's not gonna work if you can't SSH to localhost)

**->** Have you tried to SSH'ing into both (from the cmdline)?
(Same as above, cept if you can't SSH to the remote host, it won't work as well)

**->** Are you using ssh-keys and ssh-agent?  If so, is the password you're using for the keys correct?

**->** If you can SSH into both machines correctly, then try a test SCP command:
```

# to localhost first
cd
touch test
scp ~/test ~/test2
ls

```
test2 should now be in your home directory (NOTE - if test2 is already in your home directory prior to this test, then change test2 to something else)

```

# to remote host
scp ~/test mokrunka@Engineer:~/test

```

**->** If none of those work (give you the same issue), try adding a -v (verbose) flag to display what's exactly going on.  And feel free to post it here. 
```

scp -v ~/test mokrunka@Engineer:~/test

```


-**ALSO**, your SCP command needs to -r (recursive) flag to copy folders.
```

scp /home/controls/WINDOWS_FILES mokrunka@Engineer:/WINDOWS_FILES

# Needs to be

scp -r /home/controls/WINDOWS_FILES mokrunka@Engineer:/WINDOWS_FILES

```


Hope some of this helps.

---

### Post by y@w on 2008-09-29
I'm pretty sure you can't use scp to copy from a remote host to another remote host. I get the same error if I try that.. Either the source or the destination has to be local. "Permission denied, please try again." is a horribly undescriptive error, but like I said that's what I get when I do that and I have logins for both machines. I can pull the file to my local machine and then push it to the destination remote machine just fine.

---

