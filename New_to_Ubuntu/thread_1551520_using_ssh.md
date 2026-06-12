---
title: "using ssh"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by technmom on 2010-08-12
I am getting some videos from a repository on another computer. I have Ubuntu 10.04 on a dual boot system. I use terminal commands to ssh to my account on the other computer, change to the proper directory and use svn update to update the files. Then I go to to places>connect to server ssh  and open the folder for the repository so I can copy the file to my local computer. My question is: Is there a way to skip using terminal by using the connect to server. I have no idea how I would do the update.

Also I need to know how to copy when using Putty on the Windows side. I can do the update and list the files but how do I copy the file to my computer. Our internet went down and I had to use the laptop which does not have Ubuntu on it.
thanks,
Pat

---

### Post by Zeike on 2010-08-12
> **technmom said:**
> I am getting some videos from a repository on another computer. I have Ubuntu 10.04 on a dual boot system. I use terminal commands to ssh to my account on the other computer, change to the proper directory and use svn update to update the files. Then I go to to places>connect to server ssh  and open the folder for the repository so I can copy the file to my local computer. My question is: Is there a way to skip using terminal by using the connect to server. I have no idea how I would do the update.
For this you might want to try one of the nautilus version control extensions.  I'm not at my ubuntu computer right now so I don't know what they're called off the top of my head, or if it will work in a mounted ssh directory.  Try searching for nautilus-svn or something.

> Also I need to know how to copy when using Putty on the Windows side. I can do the update and list the files but how do I copy the file to my computer. Our internet went down and I had to use the laptop which does not have Ubuntu on it.
thanks,
Pat

You can use any client that supports sftp.  There is a compainion program to putty called pscp that you can use, although most regular ftp clients (filezilla, etc) also support sftp.

---

### Post by RiceMonster on 2010-08-12
If you want to transfer files over shh (scp) from your Linux box to windows, you cannot do that with PuTTY. I would reccomend using WinSCP to transfer files.

---

### Post by mapes12 on 2010-08-12
> Also I need to know how to copy when using Putty on the Windows side. Are your boxes both running Ubu, or one Ubu and the other one windoze? 

Which is client and which is host?

---

### Post by rtlustyo on 2010-08-12
It seems like just using an ftp would be the right choice here, is that an option?

---

### Post by technmom on 2010-08-13
I am not sure I explained myself well and maybe should stick to one question at a time. First I would like to do the update from the open folder on my computer. I did google and am downloading Tortoisehg-nautilis. Will this help? I downloaded it and it said it was installed but I can't see it to run it.

---

### Post by mapes12 on 2010-08-13
If you have a Ubu box connected to a windoze box and you want to copy over stuff from the windoze box to the Ubu box then you shouldn't need any applications other than what is in a standard installation. 

In the windoze box go to the folder or resource you want to access and enable "sharing" Then on the Ubu box go Places>Network>[Name of you MS workgroup]>[Name of the folder/resource] and copy across what you want.

---

