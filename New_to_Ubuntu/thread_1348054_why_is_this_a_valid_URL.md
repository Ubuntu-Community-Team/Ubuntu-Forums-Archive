---
title: "why is this a valid URL ?"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by occams_beard on 2009-12-06
Silly, non-ubuntu (but unix)  question but why is this a valid url?

[http://www.google.com//preferences?hl=en](http://www.google.com//preferences?hl=en)

Note the double forward slash.

Similarly, if I do

```
cd /home//myuser
``` 

It changes to my home dir without complaint. Why?

is /home/myuser equivalent to /home//myuser ?

---

### Post by blackened on 2009-12-06
I don't understand the question. The first example is an internet URL, the second is a place on the filesystem. They're not even related as far as addressing systems go.

---

### Post by Bachstelze on 2009-12-06
> **blackened said:**
> I don't understand the question. The first example is an internet URL, the second is a place on the filesystem. They're not even related as far as addressing systems go.

Of course they are. An URL is the path to a file on a server.

@OP: there is no real reason, that's just how it is. ;) What would you expect /home//user to point to?

---

### Post by occams_beard on 2009-12-06
Sure they are.

[http://www.example.com/subdir1/subdir2/](http://www.example.com/subdir1/subdir2/)

On the server might be reside in:

/home/example/subdir/subdir2/

So the question is why would /home/example//subdir1 be a valid path? (With double forward slash)

I assume its the same reason why [http://www.example.com//subdir1](http://www.example.com//subdir1) can be a valid URL.

---

### Post by Old *ix Geek on 2009-12-06
I think the original post is being misread.  He's referring to the DOUBLE SLASHES within the pathname, NOT at the beginning of the URL.  In other words, the slashes in red:

[http://www.google.com](http://www.google.com)**[color="red"]//[/color]**preferences?hl=en

cd /home**[color="red"]//[/color]**myuser

---

### Post by Dr. Oddbio on 2009-12-07
I don't think anyone has made that confusion.

But I just tried it with the very link to this thread.
Find a part in the URL with a single / and change it to //, takes you right back here.
Also interesting, clicking the reply button (but only after changing the URL to contain a //), retains the double //.

---

### Post by niteshifter on 2009-12-07
Hi,

It gets worse :) This is also valid:
```
cd /home/$USER////////////////temp
```
assuming there's a folder named 'temp' in $USER folder.

As to why this is valid, it has to do with parser logic and is applicable to URI path components and file system paths. What the parser does is read and store all that is between delimiters, the / characters in the case at hand. And there's the thing: There is nothing there, nothing is stored, there's no "data" there. So absolutely nothing happens, the parser keeps on reading until the end is reached or it has captured something to work with. When the end is reached the final processing is started, where the "parts" the parser has found get operated on or with.

One might be tempted to say that's an error. It could be handled as such but that needlessly complicates the logic. After all, what's the worst here? We've wasted some CPU cycles. We would:
A) Spend more cycles barking about it ;)

and

B) If there was supposed to be something in between the two / (but was left out) that would manifest as a not found error from the file system.

---

### Post by -grubby on 2009-12-07
> **Bachstelze said:**
> Of course they are. An URL is the path to a file on a server.

An URL goes wherever the software on the server says it goes. Though on some sites it's a path, that's not a hard rule.

---

### Post by Locke_99GS on 2009-12-07
// = /./

---

### Post by lotharmat on 2009-12-07
> **Locke_99GS said:**
> // = /./

Succinct! I like it!

---

