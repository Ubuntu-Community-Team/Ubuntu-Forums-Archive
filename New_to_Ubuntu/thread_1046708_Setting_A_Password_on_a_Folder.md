---
title: "Setting A Password on a Folder"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by Monark on 2009-01-21
How can I put a password on certain folders? I've put passwords on documents, but I would like to put a password on a folder or four, lol.

---

### Post by Monark on 2009-01-21
Is this even possible? I don't really like bumping my thread, but this is something I'd like to do sooner than later.

---

### Post by Facetious Falcon on 2009-01-21
Are you referring to encrypting files? If so then I don't think it's possible to encrypt a folder as such because encryption works at a basic level by scrambling all the data. Performing encryption directly on a folder would change it's properties to not being a folder. 

However if you want all files within a folder to be encrypted then that's possible using ecryptfs. It's especially easy to setup in 8.10 [here]("http://www.brighthub.com/computing/linux/articles/8958.aspx") is a link to setting it up. The encrypted folder gets mounted and unmounted on login so it won't ask for a password each time you try and go in which is what I think you want. 

I think there should be a way to do this it's just that I don't know it :(

---

### Post by Monark on 2009-01-21
> **Facetious Falcon said:**
> Are you referring to encrypting files? If so then I don't think it's possible to encrypt a folder as such because encryption works at a basic level by scrambling all the data. Performing encryption directly on a folder would change it's properties to not being a folder. 

However if you want all files within a folder to be encrypted then that's possible using ecryptfs. It's especially easy to setup in 8.10 [here]("http://www.brighthub.com/computing/linux/articles/8958.aspx") **is a link to setting it up. The encrypted folder gets mounted and unmounted on login so it won't ask for a password each time you try and go in which is what I think you want. **

I think there should be a way to do this it's just that I don't know it :(

Yeah, basically I want to have to enter a password when opening certain folders.

Thanks though, I appreciate it.

---

### Post by computermacgyver on 2009-01-22
Using ecryptfs probably provides the best security (although as noted it will not ask for the password each time. You basically mount the "private" folder, which requires a password, and then after that you can use the folder as normal.)

A simple password protection scheme (without encryption) would be to change the owner of a folder to another user and restrict read/write permissions to that user. Then you would have to sudo -u {restricted_user} to access any files from the command line, etc. I don't know how this would work with a GUI interface. You should probably just see the message permission denied when attempting to open the directory. This solution may provide some surface-level security but in actuality, anyone using a livecd/another computer could easily read the private files without a password.

So again, although it won't prompt you everytime (which in actuality might be a bit annoying) ecryptfs probably is the most secure. Anyone using a live cd or placing the harddrive in another computer would be prevented from reading the files. In addition if you generally keep the "private" directory unmounted then no other applications, etc. running as you could access the data.

---

