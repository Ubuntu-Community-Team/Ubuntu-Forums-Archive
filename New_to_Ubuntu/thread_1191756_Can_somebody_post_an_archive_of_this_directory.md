---
title: "Can somebody post an archive of this directory?"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by bhadotia on 2009-06-19
The story is that our network admin at our university has gone mad and has blocked .exe file extensions (among others such as zip, .dll). Now I'm trying to install msttcorefonts package  but am  unable to download the .exe setup files for the fonts:
```
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2009-06-19 19:20:17--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Connecting to 172.16.20.2:3128... connected.
Proxy request sent, awaiting response... 403 Forbidden
2009-06-19 19:20:17 ERROR 403: Forbidden.
```

So can someone (using jaunty) please upload an archive of the /usr/share/fonts/truetypes/msttcorefonts directory so that I can install the package simply by copying the directory and without having to download the .exe files. Please attach the archive as tar.gz (tar.bz2) as my network admin has also blocked .zip.

---

### Post by epicoder on 2009-06-19
Here you go.

---

### Post by bhadotia on 2009-06-19
> **sh228 said:**
> Here you go.

Heck the idiot has also blocked unkown formats (tar.gz is an unknown format to that fool):
```
 Response denied By Internet Security Setup for Academic Purposes.
Reason: header 'Content-Type' denied rule='Default' value='unknown/unknown'
Method: GET
Host: ubuntuforums.org
Path: /attachment.php?attachmentid=118225&d=1245426955 
```

I will have to ask you for a favour. Please rename the attachment as .pdf because I know that this format works.

---

### Post by epicoder on 2009-06-19
The directory is too large to upload. The reason I was able to get it earlier was that I accidentally archived the exe. Can you run an exe?

---

### Post by bhadotia on 2009-06-19
> **sh228 said:**
> The directory is too large to upload. The reason I was able to get it earlier was that I accidentally archived the exe. Can you run an exe?

Yeah I can extract it using cabextract.

But when you upload the archives please rename their extensions as .png or .pdf so that I can download them easily. After downloading I will simply rename them as whatever archive format you used, so don't forget to tell me what archive format you actually used.

---

### Post by epicoder on 2009-06-19
The uploader tests the file and can tell if it isn't an actually the file that it's extension shows.

Looks like you're boned.

---

### Post by QIII on 2009-06-19
This may be coming out of left field, but might I suggest something?

Your network admin has a reason for doing what he has done.  It could be at the behest of someone for whom he works, which is in turn at the behest of someone for whom he works.

I would suggest that you may be playing with fire by trying to enlist the help of someone here to attempt to thwart the proscription -- and making someone here complicit in attempting to violate your university's policy.

It might be better to make a request directly to your admin for an exception.

---

### Post by bhadotia on 2009-06-20
> **QIII said:**
> This may be coming out of left field, but might I suggest something?

Your network admin has a reason for doing what he has done.  It could be at the behest of someone for whom he works, which is in turn at the behest of someone for whom he works.

I would suggest that you may be playing with fire by trying to enlist the help of someone here to attempt to thwart the proscription -- and making someone here complicit in attempting to violate your university's policy.

It might be better to make a request directly to your admin for an exception.


You see it not that serious an issue as you seeing it (or trying to make it). The only thing is that our university (which is government organization) recently hired a private firm to manage our network. And since these idiots took over they have caused nothing but havoc and invonvience for students. We can very  easily make them unblock every thing (even pornography) but at the present moment vacations are on and only those of us who have to do training here are staying so they don't listen to our complains as they are few and this foolishness started only after the beginning of the vacations.
 
You can very easily understand that blocking P2P/pornography/movies is acceptable (and this was the situation before they came) but where is the point in blocking .exe/.zip. Is that not insanity:D?

Anyways thanks for the help!):P

---

### Post by bhadotia on 2009-06-21
You can download these fonts in tar.gz format from [freshmeat]("http://freshmeat.net/projects/msfonts/").

---

### Post by zerhacke on 2009-06-21
> **bhadotia said:**
> Is that not insanity:D?
Anyways thanks for the help!):P
I wouldn't say keeping your job by doing what you're told instead of listening to a student is insane.  Pray tell, do you know how many people get infected with malware on a Windows network by downloading exe files?  You're asking him to put his entire network at risk.  I wouldn't do it either.

---

### Post by bhadotia on 2009-06-21
> **zerhacke said:**
> I wouldn't say keeping your job by doing what you're told instead of listening to a student is insane.  Pray tell, do you know how many people get infected with malware on a Windows network by downloading exe files?  You're asking him to put his entire network at risk.  I wouldn't do it either.

Guess I can't imagine that as I'm not a network admin. ;)

But I think you are one. So do you block .exe on your network too. But how do your users download windows programs if you do that.

---

