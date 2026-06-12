---
title: "GPG NO_PUBKEY Error; Fresh install of 9.10, now getting errors when updating"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by steve228 on 2010-03-20
Ok I did a fresh install of 9.10 Ubuntu recently.  I saved my sources.list so I wouldn't have to go digging through and find the repo's and everything.  However, I forgot about the keys and having to add them.  

So here is my problem.  I keep getting this error message when I update:
> 
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C41B720D95628707

I have tried google and everything else to try and figure out how to add they key but no luck.  

I even downloaded an automated script (which was amazing and took care of about 15 missing keys for me) [_**Script to get GPG Keys**_]("http://popey.com/blog/2009/06/05/Easy_Script_To_Get_And_Install_PPA_GPG_Keys/")

The script above found all of them but that one.  Is there any way that I can fix this?  Maybe somebody here has the same problem with this particular GPG error?... 


Thanks in advance,
Steve

---

### Post by hictio on 2010-03-20
I had the same problem on Jaunty, don't recall why, tho...
Here is what I did to overcome the problem, on a Terminal, on the box you are having problems, while connected to the internet:

```

gpg --keyserver keyserver.ubuntu.com --recv-keys Problem.Key
gpg --export --armor Problem.Key | sudo apt-key add -

```

Replace "Problem.Key" with the Key ID you are having problems, that is: C41B720D95628707

Hope this helps.

---

### Post by steve228 on 2010-03-21
Thanks a ton!  Worked great.  Changing thread to solved :-)

---

