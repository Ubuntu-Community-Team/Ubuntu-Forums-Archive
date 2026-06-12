---
title: "Delete then reinstall Firefox"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by Segofam on 2011-08-13
How do I delete and reinstall Firefox?

I cannot connect to the work servers, I keep getting this SSL error, or at last attempt a missing add-on!

If I can delete Firefox, then reinstall it, I think I might be able to start a-fresh and go on from there.

If you have any other good suggestions, let me know!

Anyone know what all the certificates are for in security in Firefix?

Sincerely,

Scott.

---

### Post by raja.genupula on 2011-08-13
```
sudo apt-get remove firefox 
```
it removes firefox

---

### Post by Carborundum on 2011-08-13
```
sudo apt-get purge firefox
```Same as above, except it also removes configuration files.

---

### Post by Segofam on 2011-08-13
Thanks folks,
I thought the apt-get was for downloading and installing...just learnt something new :)
I guess 'apt-get install firefox' puts it back?
Scott

---

### Post by Carborundum on 2011-08-13
Yep.

---

### Post by raja.genupula on 2011-08-13
> **Carborundum said:**
> ```
sudo apt-get purge firefox
```Same as above, except it also removes configuration files.

aah ! thanks for this

---

### Post by Segofam on 2011-08-13
Ok!
Well, good news, it uninstalled and installed well, but I still can't log into our work servers.
I am going to close this thread and open another one, hoping that someone will help me solve the SSL error issue.
Thanks for your help.

Ok, back again..
The uninstall and reinstall worked great...now to the bottom of the thread as requested...

---

### Post by amjjawad on 2011-08-13
Please let us know if re-installing Firefox solved the issue :)

---

### Post by amjjawad on 2011-08-13
> **Segofam said:**
> Ok!
Well, good news, it uninstalled and installed well, but I still can't log into our work servers.
I am going to close this thread and open another one, hoping that someone will help me solve the SSL error issue.
Thanks for your help.

NO NEED to open NEW thread. You already stated the problem in your first post so why new one?

---

### Post by amjjawad on 2011-08-13
Instead, I suggest to search here for similar issues:

[www.googlubuntu.com](www.googlubuntu.com)

---

### Post by Segofam on 2011-08-13
...and my other problem with the server error is...

ok, so I cant paste a screen shot, or insert a pic, so I will type it out:

You have not chosen to trust "VeriSign Class 3 Extended Validation SSL CA", the issuer of the server's security certificate (SSL erro 61)

I can get to the site, but I can't log onto the profile.

Scott.

---

### Post by amjjawad on 2011-08-13
> **Segofam said:**
> ok, so I cant paste a screen shot, or insert a pic, so I will type it out:

Scott.

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=8046[/IMG]



[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=8047[/IMG]

---

### Post by Segofam on 2011-08-13
Ok!
I attached the screenshot of the error message...not sure how to get it in here, I will submit this and see what happens!

Ok, so you have to click the attached thumbnail to view it. How did you get that screenshot in here?

---

### Post by amjjawad on 2011-08-13
> **Segofam said:**
> Ok!
I attached the screenshot of the error message...not sure how to get it in here, I will submit this and see what happens!

Ok, so you have to click the attached thumbnail to view it. How did you get that screenshot in here?

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=8147[/IMG]


I use the Albums features in this forum. You need to insert the link of the image.
If you can't, just attach :)

You have two options to attach/include a screenshot on this forum :)

---

### Post by Segofam on 2011-08-13
> **amjjawad said:**
> [IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=8147[/IMG]


I use the Albums features in this forum. You need to insert the link of the image.
If you can't, just attach :)

You have two options to attach/include a screenshot on this forum :)

Thanks for the extra lessons here, much appreciated.
I can't get it to insert a pic from my desktop, so I will go with the attachment :)

Ages ago I put a copy and paste out of the command line in here I am sure! Wonder why it won't do it now!!!

Anyway...moving on...

---

### Post by amjjawad on 2011-08-13
> **Segofam said:**
> Thanks for the extra lessons here, much appreciated.

You welcome and these are not lessons, just few tips :D

> I can't get it to insert a pic from my desktop, so I will go with the attachment :)

No, not from your Desktop, it should be URL (Please enter the URL of your image).

Yes, you can go for the attachment because it's easier and faster sometimes.

> Ages ago I put a copy and paste out of the command line in here I am sure! Wonder why it won't do it now!!!

You mean like this:

```
sudo apt-get update

```

You need to use CODE tags OR highlight the text and click "#".

I hope that what you meant :)

---

### Post by Elfy on 2011-08-13
To completely purge you would also need to remove the .mozilla folder in your home which would also lose any personal customisation. 

Try starting firefox from a terminal with -safe-mode see if you can get there then.

firefox -safe-mode

You could also perhaps look into the certificates you've got in firefox preferences > advanced > encryption - perhaps delete the one causing the issue and try again. You should be able to, if necessary set it to allow it once. 

If you still have issues - do you only get the issue with the one PC - have you tried any others?

---

### Post by amjjawad on 2011-08-13
This might help?

[http://www.google.com/search?q=VeriSign+Class+3+Extended+Validation+SSL+CA&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=VeriSign+Class+3+Extended+Validation+SSL+CA&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

I searched on google for this: VeriSign Class 3 Extended Validation SSL CA

---

### Post by SoFl W on 2011-08-13
Why are you choosing not to trust *'"VeriSign Class 3 Extended Validation SSL CA", the issuer of the server's security certificate (SSL erro 61)*'?

---

### Post by SoFl W on 2011-08-13
see:
[http://ubuntuforums.org/showthread.php?t=912886](http://ubuntuforums.org/showthread.php?t=912886)
[http://geekpete.com/blog/tech-guides/linux-citrix-client-error-61-ubuntu-810-intrepid-ibex](http://geekpete.com/blog/tech-guides/linux-citrix-client-error-61-ubuntu-810-intrepid-ibex)
[http://ubuntuforums.org/showthread.php?t=1105855](http://ubuntuforums.org/showthread.php?t=1105855)

---

### Post by Segofam on 2011-08-13
> **forestpiskie said:**
> To completely purge you would also need to remove the .mozilla folder in your home which would also lose any personal customisation. 

Try starting firefox from a terminal with -safe-mode see if you can get there then.

firefox -safe-mode

You could also perhaps look into the certificates you've got in firefox preferences > advanced > encryption - perhaps delete the one causing the issue and try again. You should be able to, if necessary set it to allow it once. 

If you still have issues - do you only get the issue with the one PC - have you tried any others?

I got the same error message when attempting to connect with firefox -safe-mode

I still have xp on this laptop - rarely used - and I can get into my work profile from it, and I can use our old pc which I rebuilt and put Win7 on it recently, it's the Enterprise version from a friend. There is no problem getting in using IE.

I don't know anything about certificates!
If I delete them all, will they come back like cookies do when I go to log into pages etc?

---

### Post by Segofam on 2011-08-13
> **SoFl W said:**
> Why are you choosing not to trust *'"VeriSign Class 3 Extended Validation SSL CA", the issuer of the server's security certificate (SSL erro 61)*'?

I believe I did choose to trust!

---

### Post by Segofam on 2011-08-13
> **Segofam said:**
> I believe I did choose to trust!

The attached is what I am now receiving...

---

### Post by Segofam on 2011-08-14
Ok...

I went through the links posted in the thread, and if I were a little more familiar with the terms, it might have helped!

What if I reloaded my system...does anyone believe that would work?

---

