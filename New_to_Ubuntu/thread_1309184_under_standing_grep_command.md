---
title: "under standing grep command"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by SpinningAround on 2009-11-01
I'm trying to figure out how grep -q work, if lets say 
```
grep -q cake
```
is found will status be 0 but will happen if it's not found and where do I read this status?

---

### Post by Rayve on 2009-11-01
Ubuntu Community has some great documentation on various commands - see here for their grep entry: [https://help.ubuntu.com/community/grep](https://help.ubuntu.com/community/grep)
And the wikipedia entry: [http://en.wikipedia.org/wiki/Grep](http://en.wikipedia.org/wiki/Grep)

But I think, not positive, that if grep does not encounter any matching strings, there will simply be no return text.  I don't think there is a "verbose" option for grep, so to speak, to make it return a "Search string not found".

Edit: Because I'm half asleep and apparently can't read this morning... (and I'm learning more about grep, also!) "grep -q" gives us:
> 
**-q**Quiet. Nothing shall be written to the standard output, regardless of matching lines. Exit with zero status if an input line is selected.So regardless of whether it finds anything or not, there won't be anything written to the console.

I'm not sure if that answers your question?

---

### Post by Joeb454 on 2009-11-01
I imagine grep -q is of more use in a bash script or if you want to redirect output to a file.

That said, even if you did want to output to a file, I imagine there wouldn't be a whole lot of point using -q then either ;)

---

### Post by Joeb454 on 2009-11-01
I imagine grep -q is of more use in a bash script or if you want to redirect output to a file.

That said, even if you did want to output to a file, I imagine there wouldn't be a whole lot of point using -q then either ;)

---

### Post by kevdog on 2009-11-01
Can you tell us what you are trying to do so we could be more help?

---

### Post by slakkie on 2009-11-01
Hi, you need to look at the exit code of grep

```

grep -q "lucid" /etc/apt/sources.list
[ $? -eq 0 ] && echo found lucid

grep -q "karmic" /etc/apt/sources.list
[ $? -ne 0 ] && echo did not find karmic

```

You could also echo $? right after the grep command, it will show you the exit value of grep. 0 on success, 1 on failure. See man grep for more details.

---

### Post by SpinningAround on 2009-11-01
I have a bit problem figuring out exactly what is happening, in the following code will grep find lo but not ppp0 yet the same message/info is returned.


```

:~$ l=$(ifconfig | grep -q lo)
:~$ echo $l
//nothing (0) I guess
:~$ l=$(ifconfig | grep -q ppp0)
:~$ echo $l
//also 0 even if ppp0 don't exist 

```

If you wonder what I'm doing am I trying to create a script that check if ppp0 is active or not.

---

### Post by slakkie on 2009-11-01
grep -q will not show anything. You need to look at the exit code to see if something was found. Remove the -q from your statements and retry it. See what happens now.

---

### Post by SpinningAround on 2009-11-01
> **slakkie said:**
> grep -q will not show anything. You need to look at the exit code to see if something was found. Remove the -q from your statements and retry it. See what happens now.

How do I look at the exit code? :confused:

---

### Post by slakkie on 2009-11-01
> **SpinningAround said:**
> How do I look at the exit code? :confused:

By looking at the $? var.

```

grep karmic /etc/apt/sources.list
echo $? # 0 if karmic is found, 1 if it isn't.

```

---

### Post by SpinningAround on 2009-11-02
thanks :)

---

