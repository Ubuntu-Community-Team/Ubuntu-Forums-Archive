---
title: "open a GUI window using terminal"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by paul88 on 2010-05-15
Is there anyway on opening a GUI for a folder that you are in. Such as if i direct to the home directory and then type the command then a GUI of the directory appears.

Thanks

---

### Post by angry_johnnie on 2010-05-15
```
nautilus /whichever/directory/you/are/in
```

replace "nautilus"  with "your-file-manager"

---

### Post by BoneKracker on 2010-05-15
$(pwd) returns the directory your currently in.

. is also a synonym for the current directory.

So I think the following would also work```
nautilus $(pwd)
``````
nautilus .
```
Also, if you want the graphical process to fork off, so you can close the terminal (or continue doing something else with it), you can add an ampersand to the end of the command:```
nautilus . &
```

---

### Post by tgalati4 on 2010-05-15
```

nau(tab) . &

```

I can do that in 6 keystrokes.

---

### Post by BoneKracker on 2010-05-16
> **tgalati4 said:**
> ```

nau(tab) . &

```

I can do that in 6 keystrokes.

:lol:

You forgot to count <Enter>.

I can do it in 5.

ctrl+r na <Enter>

And then 2.

up-arrow <Enter>

:P

Except I don't have nautilus on my computer, or any other file manager, for that matter.  I don't like file managers.

---

### Post by TironN on 2010-05-16
> **BoneKracker said:**
> :lol:

You forgot to count <Enter>.

I can do it in 5.

ctrl+r na <Enter>

And then 2.

up-arrow <Enter>

:P

Except I don't have nautilus on my computer, or any other file manager, for that matter.  I don't like file managers.

No file manager?

Now thats a hardcore terminal user!

---

### Post by BoneKracker on 2010-05-16
They just get in the way and slow you down.  It's like having somebody holding a a map in front of your face when you're trying to drive.

---

### Post by TironN on 2010-05-16
Yeah. I get what your saying. I am still not quite fast enough at the terminal to do it yet but one day!

---

### Post by MrWES on 2010-05-16
> **tgalati4 said:**
> ```

nau(tab) . &

```

I can do that in 6 keystrokes.


```
alias nat='nau(tab) . &'
```

three keystrokes :)

---

### Post by tgalati4 on 2010-05-16
Yea, I was going to include an alias for "n" but then that would be cheating.

---

### Post by BoneKracker on 2010-05-16
> **tgalati4 said:**
> Yea, I was going to include an alias for "n" but then that would be cheating.

++

cheating

:lol:

(so were my last 2 though)

---

### Post by MrWES on 2010-05-18
> **tgalati4 said:**
> Yea, I was going to include an alias for "n" but then that would be cheating.

heh.... don't think I could top that one.

---

### Post by BoneKracker on 2010-05-18
> **MrWES said:**
> heh.... don't think I could top that one.

How about a motion-sensor/facial-recognition app that launches it when when you twitch your nostrils?

0 keystrokes.

And biometric authentication as a bonus.

---

