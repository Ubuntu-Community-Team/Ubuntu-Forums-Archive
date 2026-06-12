---
title: "Open Office Read Only"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by CryptiniteDemon on 2009-03-05
Whenever I open a document from the web (like an email attachment) open office opens it as read only.

Is there any way to set it so that it opens as a writable?  It's annoying to have to save it to my desktop first to edit.

---

### Post by cwsnyder on 2009-03-05
The only way to open a document as writeable is to have permission to write to the place where the document resides.  If you cannot write directly to your inbox on the web, for example, you have to copy it to a location where you can write to edit.  The same thing will occur if you attempt to open a document off of a CD-ROM.

---

### Post by EssexEagle on 2009-03-05
I just tried opening an e-mail attachment in OpenOffice, going to the /tmp folder and changing the file's permissions from -r-------- to -rw-------, but OpenOffice said the file was still read-only, even when I did File > Reload.  Can someone explain why this doesn't work?

(Sorry by the way that this doesn't answer the question, I'm just curious as to why my idea didn't work.)

---

### Post by cwsnyder on 2009-03-06
> **EssexEagle said:**
> I just tried opening an e-mail attachment in OpenOffice, going to the /tmp folder and changing the file's permissions from -r-------- to -rw-------, but OpenOffice said the file was still read-only, even when I did File > Reload.  Can someone explain why this doesn't work?

(Sorry by the way that this doesn't answer the question, I'm just curious as to why my idea didn't work.)
The only problem with your idea is you did not change your permission on the **folder**.  If you were not logged in as root or ran your load of OpenOffice.org as sudo, you do not have permission to write to the /tmp folder, just folders off of your ~ directory.

---

### Post by EssexEagle on 2009-03-06
> **cwsnyder said:**
> The only problem with your idea is you did not change your permission on the **folder**.  If you were not logged in as root or ran your load of OpenOffice.org as sudo, you do not have permission to write to the /tmp folder, just folders off of your ~ directory.

I see.  Thanks! :)

---

### Post by CryptiniteDemon on 2009-03-28
> **cwsnyder said:**
> The only way to open a document as writeable is to have permission to write to the place where the document resides.  If you cannot write directly to your inbox on the web, for example, you have to copy it to a location where you can write to edit.  The same thing will occur if you attempt to open a document off of a CD-ROM.

Yeah, I know this.  But I can open a protected .txt in gedit and make all the changes I want.  It just won't save it.

What I'm annoyed about is that open office doesn't let me make any changes to the friggin document.  A lot of times I want to change stuff in a document, but I don't want to save it.  I just want to see the effect of something really quick and it's annoying when I have to go and save it elsewhere.

---

