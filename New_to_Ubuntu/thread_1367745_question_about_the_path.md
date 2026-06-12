---
title: "question about the path"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by thungmail on 2009-12-29
Hi 
I do some basic reading about the Linux,there is a path like this
```

~/script (script is a name of folder )

```

I would like to ask that what is ~/script and is it ~/script as same as /script 
Thanks

---

### Post by taurus on 2009-12-29
The ~ means your $HOME so if your username is john, then ~/script is the same as /home/john/script.  So as you see, ~/script is not the same as /script.

---

### Post by stlsaint on 2009-12-29
this symbol (~) is root meaning the root of your profile or 
/home/user. This /script (or name of folder) would be a directory...see the absence of ~. meaning this can be /home/user/Desktop/mystuff!

so ~ is root level and 
/script is a directory or folder inside another folder.
Hope i didnt just say that so you cant understand or is confusing even more!

---

### Post by taurus on 2009-12-29
> **stlsaint said:**
> this symbol (~) is root meaning the root of your profile or 
/home/user. This /script (or name of folder) would be a directory...**see the absence of ~. meaning this can be /home/user/Desktop/mystuff**!

so ~ is root level and 
/script is a directory or folder inside another folder.
Hope i didnt just say that so you cant understand or is confusing even more!

Actually, I have to disagree on that.  So you're saying that /mystuff could be the same as /home/user/Desktop/mystuff?

The / in front of mystuff is the root directory, way at the top.

---

### Post by stlsaint on 2009-12-29
> **taurus said:**
> Actually, I have to disagree on that.  So you're saying that /mystuff could be the same as /home/user/Desktop/mystuff?

The / in front of mystuff is the root directory, way at the top.


No they are not the same, but yes if you do cd /mystuff inside the Desktop and cd /home/user/Desktop/mystuff from root then you shall end up in the same directory. just because (/) is in front doesnt mean you are starting from /home/user. but yes it is root directory of whatever directory you have changed into.

---

### Post by taurus on 2009-12-29
Again, sorry but "cd /mystuff" (even if you are in ~/Desktop when you run that command) and "cd /home/user/Desktop/mystuff" is _not_ the same.

However, this is the same

```
cd ~/Desktop
cd mystuff
```
as
```
cd ~/Desktop/mystuff
-or-
cd /home/user/Desktop/mystuff
```

---

### Post by stlsaint on 2009-12-29
> **taurus said:**
> Again, sorry but "cd /mystuff" (even if you are in ~/Desktop when you run that command) and "cd /home/user/Desktop/mystuff" is _not_ the same.

However, this is the same

```
cd ~/Desktop
cd mystuff
```
as
```
cd ~/Desktop/mystuff
-or-
cd /home/user/Desktop/mystuff
```


It seems my wording came across wrong because thats exactly what i was saying or trying to at least...if your explanation is what the poster understands than by all means i point to your post as the answer to original question.
Thanks

---

### Post by bodhi.zazen on 2009-12-29
> **thungmail said:**
> Hi 
I do some basic reading about the Linux,there is a path like this
```

~/script (script is a name of folder )

```I would like to ask that what is ~/script and is it ~/script as same as /script 
Thanks

By default most distros use ~/bin as the default location for scripts. There is not ~/bin by default, but if you add it it will be added to your path the next time you log in or start a shell.

so ..

```
mkdir ~/bin
```

put your scripts in ~/bin

---

### Post by thungmail on 2009-12-31
Now I learnt from what you were discussing. Thanks for your anwser

---

