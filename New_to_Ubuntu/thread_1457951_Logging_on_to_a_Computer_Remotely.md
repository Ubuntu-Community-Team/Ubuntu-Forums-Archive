---
title: "Logging on to a Computer Remotely"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by newport_j on 2010-04-19
I am trying to use another employee's computer remotely and I am having some trouble. He reinstalled 32 Ubuntu 9.04 recently and we are trying to establish a re-connection.

I have not messed with the software (or its configuration) on my computer, but, of course, the host computer had a 32 bit version of CUDA installed.

Here is the dialog that I get when I try and sign on:

james ~$ ssh -X Rowester
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
ae:4e:d6:bd:00:40:8f:40:8c:1d:a6:29:55:3d:04:9d.
Please contact your system administrator.
Add correct host key in /home/james/.ssh/known_hosts to get rid of this message.
Offending key in /home/james/.ssh/known_hosts:1
RSA host key for 129.190.170.143 has changed and you have requested strict checking.
Host key verification failed.

The known_hosts file is:

|1|tnfhEX9uwseczord4veBn4OuYmQ=|Ydldz4Mtc0I2Bn9aOJg3WWonLZ4= ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAxGkff6NUi+OORB+bclWUnn4USnNDCo99uk9ut1D9Qh/yIGHWKQ7DrcowGx9oM++8I1wAkC7ylqg9YEog4KoQk5WEbARqpO8ZzMw/DJmkPk/lqtZhTsKSLZc54Fplq7KRtH6OlEqAVD1m+RhR3CxSYyUSyL3Mfydn0sLlwppkYMP8jZtYAlZYP0sfHLkaEy14oHy6XtxTPrFFyAU5eYpe/GVWFirCveH/iEtVDkC24HeDMty/Ki3sHxd59bFk3LHDCUQ6sUfhdT6NZx3LueAw+0Gl8WfKr05ZHSsHB5679ldysXIbjReMlycog7XRLyIAsZf6FiJcYG9x0pw2G8VXaQ==

I am not sure what is happening. I do not know what the initial message after ssh -X Rowester is talking about. 

Any help appreciated to get back on line, remotely.

Newport_j

---

### Post by talonmies on 2010-04-19
When the OS was reinstalled, a new ssh key pair for the ssh server was generated during the installation process. Your ssh client keeps a list of "safe to use" hosts and their keys. It does so to prevent any third party machine from impersonating the "trusted" host. Now it is detected that a machine you previously said was safe has changed its key, which might mean something bad. That is the source of the error.

In your home directory is a hidden subdirectory called .ssh . Inside is a file called known_hosts. Edit that file and delete the entry at line 1. Next time you ssh, you will be asked whether the key is safe, answer yes and it will work again.

For future reference this is described in detail in the ssh man page.

---

### Post by Gaweph on 2010-04-19
Yup, this is actually a security thing.  It is trying to prevent a man in the middle attack.

as previously stated you can remove the line, feel free to delete the whole .ssh folder if you have not used ssh for anything else, and it will just be re created next time.

Gaw

---

### Post by newport_j on 2010-04-19
Yes, that worked.

newport_j

---

### Post by Iowan on 2010-04-19
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")? :)

---

