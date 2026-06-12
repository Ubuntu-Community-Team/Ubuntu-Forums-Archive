---
title: "Sorry if you've heard this one"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by luciano991 on 2009-08-29
Hi,

I have been prowling the forums and other resources and I have come up with some partial solutions to my inquiry about setting up a file server. But nothing quite nails it for me yet. 

I have an old PC I'm turning into a file server. Have Ubuntu 9.04 desktop installed. Have read a bit about Samba. Have both a Windows machine and a Mac that want to use the file server. I have a hard drive I was using in the PC as storage drive with data on it I don't want to lose. Have another 500GB hard drive that I would like to add for storage and a 120GB drive that holds the Ubuntu installation. 

I want to be able to access NTFS drives over the network from the mac and the PC. Have done some reading about UFS and other formatting systems. Can I take the data from my NTFS drive and port it over to a different file system?

So I think you get the picture and I'm not necessarily looking for a blow by blow but if can point me in the right direction I'm more than willing to be educated.

Thanks,

Luciano

---

### Post by cariboo on 2009-08-30
Samba doesn't care what the file system is. I have the drives in my server formatted as XFS, all the computers on my network can access to the files on the server.

---

