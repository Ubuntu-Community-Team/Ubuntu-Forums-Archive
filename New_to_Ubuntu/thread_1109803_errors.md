---
title: "errors"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by TheNeo on 2009-03-29
Alright well I'm brand new to Ubuntu. I had way to many errors with Vista so decided to try it out. I was trying out fprint-demo to see if my digitalpersona scanner would work, but no avail. Anyways I ran update afterwards and keep getting this..

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 084AF32EC2A6B0B1


I've removed fprint, but still get this error not sure what it means. Also, is there a way to get a mentor? I've seen offering mentoring, but I was more interested at learning how to program in and with Ubuntu. I'm a novice in C++ and learning C# now. I also downloaded eclipse and monodevelop and it looks like mono is the better choice because it has more of a VS feel. Also, I've read about code::blocks any idea what they are? I know its alot for one post but thought I'd get it out there to jump in a figure this **** out. Thanks for any help.

---

### Post by directhex on 2009-03-29
You're getting that warning because a package repository you have configured is cryptographically signed (for security) but you don't have that signature in the list of ones you trust.

The following voodoo in a terminal will download and trust the signature:

```
gpg --recv-keys 084AF32EC2A6B0B1
gpg --armour --export 084AF32EC2A6B0B1 | sudo apt-key add -
```

---

### Post by eragon100 on 2009-03-29
> **TheNeo said:**
> Alright well I'm brand new to Ubuntu. I had way to many errors with Vista so decided to try it out. I was trying out fprint-demo to see if my digitalpersona scanner would work, but no avail. Anyways I ran update afterwards and keep getting this..

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 084AF32EC2A6B0B1


I've removed fprint, but still get this error not sure what it means. Also, is there a way to get a mentor? I've seen offering mentoring, but I was more interested at learning how to program in and with Ubuntu. I'm a novice in C++ and learning C# now. I also downloaded eclipse and monodevelop and it looks like mono is the better choice because it has more of a VS feel. Also, I've read about code::blocks any idea what they are? I know its alot for one post but thought I'd get it out there to jump in a figure this **** out. Thanks for any help.

You can ignore that "error" from the update-manager. I get it too, but it isn't important.

Code::Blocks is a good IDE for C++, but do keep in mind that a lot of linux programs, including all of the ubuntu system tools such as the installer, update-manager, and driver manager are written in python, a very simple to use but powerfull interpreted language that comes installed by default with ubuntu. My favourite IDE for it is SPE, just install it from add/remove software, but there are others. There is a huge amount of modules for it which allow you to ceate anything from 3d first person shooters to music players.

If you already know C++, it will be easy to learn python, because they resemble each other. Python has a lot cleaner syntax tough. Just search google for "python tutorial" or something similar and get started.

If you really want to use C++, go with Code::Blocks or monodevelop for C#.
I would recommend python, tough.

---

### Post by TheNeo on 2009-03-30
Well first off thank both of you for the quick reply and directhex thanks for the fix. It took me a couple of runs for some reason, but it eventually worked. Maybe because I signed in as root then it worked? not sure but heh no more annoying error pop up. I understand the need for python and I will eventually get to it. I'm currently in school in a gaming program so C++ and C# is what we are learning. To get mentored on here I would have to understand Python first is that what I'm hearing? If so thanks for the reply.

---

### Post by directhex on 2009-03-30
> **TheNeo said:**
> Well first off thank both of you for the quick reply and directhex thanks for the fix. It took me a couple of runs for some reason, but it eventually worked. Maybe because I signed in as root then it worked? not sure but heh no more annoying error pop up. I understand the need for python and I will eventually get to it. I'm currently in school in a gaming program so C++ and C# is what we are learning. To get mentored on here I would have to understand Python first is that what I'm hearing? If so thanks for the reply.

"monodevelop" is a package containing an IDE similar to SharpDevelop. It contains a GUI designer (GTK#) and will pull in a C# compiler. If you want to go down the C# route, that's your best bet.

---

### Post by hyper_ch on 2009-03-30
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

