---
title: "A couple of beginer questions"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by Jon Anderson on 2011-02-15
I see all  these computer language inside of boxes on many of the forums . I would guess that they are made to be copied and pasted into a program or some place.  Can you tell me when you get these lines of computer language, were do you put it and if there is 2-3 boxes in the message does that mean to copy the first box and bring it to were its suppose and paste it, then go back and retrieve the second box and paste it and so on. They also talk about the command line, is that the command line in the boot up page (I think typing in C). Is terminal another way to get to command line, if not what is terminal used for?

---

### Post by sanderd17 on 2011-02-15
[http://linuxcommand.org/](http://linuxcommand.org/)

read this to get info on the command line. to start the command line under ubuntu, press CTRL+ALT+T or search it in the menu's under the name "terminal".

---

### Post by scouser27 on 2011-02-15
Terminal provides you with a command line.

Unless you're specifically told that you're interacting with Grub or whatever bootloader you have installed, then most of the time you'll be interacting with the commandline.

Copy and paste is a bad idea most of the time as you can miss bits if you don't select the full line. Unless you have a very specific and very long command, I'd type it in.

---

### Post by sikander3786 on 2011-02-15
Yes the language inside ```
 tags are commands and they are meant to be pasted in Applications > Accessories > Terminal.

[code]e.g, this one
```

But don't blindly follow any command from any website other than ubuntuforums as you don't know what that command is going to do.

Neither blindly follow any command from the forums also unless you exactly you've got the same issue. If you are not sure, feel free to post a new Thread and let the mates answer you specifically.

For copying the commands, you can highlight a line in your browser, open up Terminal and just hit middle-click button on your mouse. Or you can simply copy/paste.

The commands that look like this.

```
command 1
command 2
command 3
```

They need to be copied one by one and after the prior one has completed its operation and you are returned to your user@computer: prompt in Terminal.

And when running a command as super-user with a sudo in front e.g,

```
sudo command
```

It would ask for your password in the Terminal and when you type it, you _wont_ see any characters or asterisks. You just need to type blindly and hit <Enter>.

---

### Post by kn0w-b1nary on 2011-02-15
It depends. Usually a different line is a new command to be executed after the previous. Copy-Paste may work, but not the best way to go.

Hope this helps!

---

### Post by sikander3786 on 2011-02-15
> **scouser27 said:**
> Copy and paste is a bad idea most of the time as you can miss bits if you don't select the full line. Unless you have a very specific and very long command, I'd type it in.

I would rather say copy/paste is better for beginners as you are not going to mis-type anything or change case as Linux is case sensitive ;-)

---

### Post by lisati on 2011-02-15
> **scouser27 said:**
> 
Copy and paste is a bad idea most of the time as you can miss bits if you don't select the full line.
It's a matter of personal choice: I would tend to advise "copy and paste" in some situations, because there are times when it's more reliable.

I've lost count of the times I've seen someone ask for the output of something like **fdisk -l** and the person responding has misread it as **fdisk -1**.

---

### Post by wep940 on 2011-02-15
I think it really depends on the users familiarity with Linux as to whether they should use copy and paste.  There are a lot of new users out there that don't see the spaces in a command line, don't know where the piping symbol is, etc.  For those users, and in watching the forum for many years there have been a lot, cut and paste is the way to go *IF* they remember one line at a time, stop if something errors out.
 
Just my 2-cents worth.

---

### Post by Paqman on 2011-02-15
Feel free to ask for an explanation of the commands people post, too. People shouldn't ever post commands without explaining them in this forum, but it happens all the time. Don't run it until they've  actually taken the time to explain it.

---

### Post by cariboo on 2011-02-15
I would suggest, that unless the op specifies what version he/she is running, we assume they are running Ubuntu, and give both a command line and gui solution to their problem.

---

### Post by sikander3786 on 2011-02-15
> **cariboo907 said:**
> I would suggest, that unless the op specifies what version he/she is running, we assume they are running Ubuntu, and give both a command line and gui solution to their problem.
I agree 100 % but most of the members are in a hurry and in the limited free time, they try to help as much users as they can thus can't post comprehensive answers most of the time.

This is something recurrent.

[http://ubuntuforums.org/showthread.php?t=1548853](http://ubuntuforums.org/showthread.php?t=1548853)

---

### Post by wep940 on 2011-02-22
You know, I hadn't thought about that before - specific instructions yes - but not examples very often.  I must say I agree - with as much as we ask the OP's to post things for us to help solve their problems, it's probably the least we can do back for everyone who reads the thread to post some examples.  I will *try* to remember to do that.

---

