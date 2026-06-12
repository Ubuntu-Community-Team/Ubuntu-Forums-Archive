---
title: "installing a *.linux file"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by myotis on 2010-10-26
I have just downloaded a program that untars to a *.linux file.

Googling hasn't helped me find any advice on installing a file with this extension, and Ubuntu doesn't recognise it if I try and run it.

Can anyone point me towards some instructions as to what I do with this file.

Many thanks,

Graham

---

### Post by rado1 on 2010-10-26
what kind of a linux file? *.deb, *.rpm or another type?

---

### Post by SlugSlug on 2010-10-26
what program is it - you'd be better trying to get one through software centre,

if you have tried all that then you will need to make it executable,

chmod +x file

and then try execute it

./file

---

### Post by rado1 on 2010-10-26
good one SlugSlug. But still, what is a *.linux file?

---

### Post by SlugSlug on 2010-10-26
dunno what will be in it, that's really why you should stick to the software centre / aptitude

you could 
```
head file
```

to see what it really is..?

linux doesn't really use extensions

---

### Post by myotis on 2010-10-26
> **rado1 said:**
> what kind of a linux file? *.deb, *.rpm or another type?

Thanks, but I have no idea, that was the point of the question. I have never seen a file with a .linux extension.

Graham

---

### Post by rado1 on 2010-10-26
that's the point. what does he/she means? because *.deb files you just innstall with package manager, *.rpm with sudo chmode ( correct me if i'm wrong ) .

---

### Post by msaravanan77 on 2010-10-26
did you tried command called 'file <filename>'. you may get type of file info.

---

### Post by myotis on 2010-10-26
> **SlugSlug said:**
> what program is it - you'd be better trying to get one through software centre,

if you have tried all that then you will need to make it executable,

chmod +x file

and then try execute it

./file

Its the new linux version of Epidata  [http://epidata.dk/testing.php](http://epidata.dk/testing.php)

But as everyone here seems to be just as confsed as to what a *.linux file is, as I am, maybe I should ask epidata how I am meant to install it.  I had just assumed it was my ignorance about Linux install options.

Thanks,

Graham

---

### Post by rado1 on 2010-10-26
right click on the file and choose properties?

---

### Post by myotis on 2010-10-26
> **msaravanan77 said:**
> did you tried command called 'file <filename>'. you may get type of file info.

This gives me 

ELF 32 bit LSB executable , intel 80386 version 1 (SYSV) dynamically linked (uses shared libs), stripped

Thanks,

Graham

---

### Post by myotis on 2010-10-26
> **SlugSlug said:**
> dunno what will be in it, that's really why you should stick to the software centre / aptitude

you could 
```
head file
```

to see what it really is..?

linux doesn't really use extensions

head gives me hundreds of little boxes with 4 numbers in each box one in each corner. Sometimes the number is overwritten by a question mark.

Sometimes there are spaces between the boxes and othertimes there is a single letter or a question mark. 

Thanks,

Graham

---

### Post by myotis on 2010-10-26
Ah, hah, its already an executable. I assumed with the extension I had never seen it needed installed.

But it just needs extracted.

Sorry about that, I was confused by the *.linux extension.

And thanks to everyone for their help.

Graham

---

### Post by rado1 on 2010-10-26
welcome.

---

### Post by SlugSlug on 2010-10-26
looking at the link -- it's a .tgz file -- so yes it's compressed
```
epidatamanager.0.5.7.0.linux.32.tgz
```

---

### Post by myotis on 2010-10-26
> **SlugSlug said:**
> looking at the link -- it's a .tgz file -- so yes it's compressed
```
epidatamanager.0.5.7.0.linux.32.tgz
```

Yes, but when you extract it, you get this strange .linux extension, which is what had me confused.

Graham

---

### Post by fatality_uk on 2010-10-26
OK. Extract the tgx file to a new directory, right click and click "Extract here". Then using a terminal, change your working directory to the directory you just created using this command
```
cd ~/Desktop/epidatamanager.0.5.7.0.linux.32/
```

Once you are in that directory, run the command

```
./epidatamanager.0.5.7.0.i386.linux
```
and that will start the application.


Enjoy the app, whatever is it :)

---

### Post by myotis on 2010-10-26
> **fatality_uk said:**
> OK. Extract the tgx file to a new directory, right click and click "Extract here". Then using a terminal, change your working directory to the directory you just created using this command
```
cd ~/Desktop/epidatamanager.0.5.7.0.linux.32/
```

Once you are in that directory, run the command

```
./epidatamanager.0.5.7.0.i386.linux
```
and that will start the application.


Enjoy the app, whatever is it :)

Thanks, that is pretty well what I ended up doing, but would have been very very useful if I had still been struggling.

The app is a database designer/manager mainly aimed at epidemiological studies but useful in any field. It creates survey forms that can be used as paper forms or used directly on the computer. Its actually much cleverer than that description suggests.

And, although, it has a very good reputation, until now, its been Windows only. 

Thanks again,

Graham

---

### Post by fatality_uk on 2010-10-26
> **myotis said:**
> Thanks, that is pretty well what I ended up doing, but would have been very very useful if I had still been struggling.

The app is a database designer/manager mainly aimed at epidemiological studies but useful in any field. It creates survey forms that can be used as paper forms or used directly on the computer. Its actually much cleverer than that description suggests.

And, although, it has a very good reputation, until now, its been Windows only. 

Thanks again,

Graham

No problem. Glad it was sorted. If you can remember to mark the thread as solved. Cheers

---

### Post by myotis on 2010-10-26
> **fatality_uk said:**
> No problem. Glad it was sorted. If you can remember to mark the thread as solved. Cheers

Thanks again, I marked it solved over two hours ago, unless I haven't done it properly. I added solved to the front of the title in the first post.

Graham

---

### Post by myotis on 2010-10-26
> **myotis said:**
> Thanks again, I marked it solved over two hours ago, unless I haven't done it properly. I added solved to the front of the title in the first post.

Graham

Mmmm, obviously this isn't how you mark it solved as it isn't showing up in the main forum as being solved.

Maybe I', just having a bad day, but I can't see any obvious way of marking it solved, nor can I see any mention in the faqs.

But obviously, I haven't done it properly.

Graham

---

### Post by vim_lover on 2010-10-26
Click Thread Tools --> Mark this thread as solved

---

### Post by myotis on 2010-10-26
> **vim_lover said:**
> Click Thread Tools --> Mark this thread as solved

Thanks, now duly marked as solved.

Graham

---

