---
title: "Linux is to ??? as windows is to samba?"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by jimmy the saint on 2008-12-28
I'm just curious.  I know samba is for setting up sharing with windows.  Aside from nautilus' great "connect to server" feature, what is the linux equivalent?  

Thanks

JTS

---

### Post by mcduck on 2008-12-28
Samba is a re-implementation of the SMB (server message block) protocol used by Windows.

In other words, Windows uses SMB protocol to handle file & printer sharing. Samba brings support for this protocol to Linux & other operating systems (like OS X).

The question doesn't really make sense, as Windows doesn't have any commonly used tools for connecting to Linux file or printer shares. So the correct phase would be like "Samba is to Linux as SMB is to Windows", although it should be mentioned that native Linux networking doesn't really use SMB protocol which is mostly a Windows thing.

---

### Post by HavocXphere on 2008-12-28
I think the answer you're looking for is NFS.

---

### Post by hyper_ch on 2008-12-28
I don't understand the question.

---

### Post by wieman01 on 2008-12-28
I guess he was asking for something along the lines of NFS. I have never tried NFS myself and still use Samba because it simpler to set up.

---

### Post by Dedoimedo on 2008-12-28
If I get the idea of the thread title, then what you probably want is NFS ... Then again, if you elaborate a little more, it would help people answer a little better.
Dedoimedo

---

### Post by asgard_command on 2008-12-28
I thought this may be referring to ssh. I use Samba to network my ubuntu machine with a windows machine but ssh to network to other linux machines.

---

### Post by Tom--d on 2008-12-28
I think hes asking is.

Windows uses the SMB protocol.
Linux uses ?

---

### Post by jimmy the saint on 2008-12-28
Yeah, sorry for the lack of clarity.  I use ssh to network all of my linux boxes as well.  I know that SMB is windows, and that samba is basically SMB for linux and allows linux+windows networking.  I guess I was just curious as to what the SMB equivilant is for linux.  In other words, windows uses SMB, what does Linux use?  I think the NFS is what I was looking for.  It was more of a curiosity thing.
Thanks!

---

### Post by lisati on 2008-12-28
SSH and NFS have both been mentioned: I've never directly used either, haven't had the need. I have Samaba set up on my *ubuntu box to make it easier for it to interact with the Windows machines I might have hooked up to my home network.....

---

