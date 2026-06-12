---
title: "Files Password Protected"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by rawbertb on 2011-07-31
I am fairly new to Ubuntu (love it!) and not much of a computer geek.  I am using 11.04 on my laptop.  I am wondering if there is a way to make specific files password-protected (I think that is the term)?

---

### Post by gandaran on 2011-07-31
truecrypt is one of the best encrypting software, works on any OS
[http://www.truecrypt.org/](http://www.truecrypt.org/)

---

### Post by Rex Bouwense on 2011-07-31
I cannot remember reading about being able to password protect a single file but I think that you can change permissions on the file so only you can open, read, and write to it.

---

### Post by scorchgeek on 2011-07-31
TrueCrypt is great software and very secure, but it may be a little bit complicated for what you're trying to do.

Depending on the program you're using, you may have an option right there to password-protect a file. For example, in LibreOffice Writer, you can check the box "Save with Password" when doing a Save As. This is probably less secure than TrueCrypt, but you may not need that security--I don't know exactly what you want this for.

As Rex mentioned, you could also modify the file permissions so that nobody except your user account could see the file, though I'm not sure that's what you want--if you were logged in and somebody else sat down at your computer, they could read the file. If you want to know how to do that, look it up or ask for more help.

---

### Post by Rex Bouwense on 2011-07-31
I have just spent the last 15 minutes reading about True Crypt and it seems like a little overkill to hide a few files when you can change the permissions but I guess it depends upon how secure you want those couple of files and how sensitive the data that they contain is.  Good read.  I learned something so today was a good day.  Thanks gandaran.:popcorn:

---

### Post by haqking on 2011-07-31
you can use seahorse or GPG

then just right click and choose encrypt

---

### Post by rawbertb on 2011-07-31
Thanks all!  I'll try your suggestions.

---

### Post by haqking on 2011-07-31
> **rawbertb said:**
> Thanks all!  I'll try your suggestions.

i think for what you asked all you need to do is use seahorse, it is built in.

Install the seahorse-plugins, create a key

log out and back in and then you will have a encrypt option on right click

---

### Post by Paqman on 2011-07-31
> **haqking said:**
> create a key


This is done using the "Passwords and Encryption Keys" tool, by the way.

---

### Post by haqking on 2011-07-31
> **Paqman said:**
> This is done using the "Passwords and Encryption Keys" tool, by the way.


indeed, i dont do the whole step by step thing, i leave a little fo research, it aids the retention ;-) LOL

well that and i forgot to add in that step ;-)

---

