---
title: "dd mishap - how bad is it?"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by jimmy the saint on 2009-05-19
I was trying to use this command
```
sudo dd if=FaunOS-shadow-0.5.4-stable-usb.img of=/dev/sdh
```

But to save time (for some reason autocomplete wasn't working with the filename)I attempted to copy/paste the FaunOS filename into the command.  Bad idea.  For some reason gnomes terminal automatically executes a command once a paste operation is used.  STUPID!!!

Anyway, the command that was run was this
```
dd if=FaunOS-shadow-0.5.4-stable-usb.img
```

It went to work and copied 5 MBs before I could Ctrl-C it to death.  What is the default disk to write to?  Have I just trashed my boot sector?  I don't want to restart until I know how bad off I am.  I'm filing a bug about that stupid paste=run whatever the heck you have so far.

Thanks for the help

JTS

---

### Post by Mornedhel on 2009-05-19
Not a bug.

You may have copy-pasted a carriage return, however. It happens sometimes. Be very very careful when selecting some text not to go over the last character, or paste the text into an editor just to be sure.

---

### Post by jimmy the saint on 2009-05-19
It was copied from the output of the ls command.  I thought of that as well.  I typed "ls" into the terminal, did NOT run the command, highlighted it, ctrl-shift-C to copy, the ctrl-shift-V to repaste it. It automatically ran.  There were no carriage returns, unless the terminal already has one floating at the end, which I would consider to be a poor design anyway, as it would introduce this very problem.

---

### Post by Mornedhel on 2009-05-19
> **jimmy the saint said:**
> There were no carriage returns, unless the terminal already has one floating at the end, which I would consider to be a poor design anyway, as it would introduce this very problem.

I don't think it has, AFAIK. I'm not an expert, so I may be wrong, but there is no reason to do that and I don't see how it would make the programmer's job easier, either.

Anyway.

The dd manpage says 'of=FILE -- write to FILE instead of stdout'

So I'm guessing it just displayed some garbage on the terminal since you didn't provide 'of'. You should be safe.

Side note : some commands have smart autocompletion, for instance mplayer autocompletes on video files, etc. When I'm trying to autocomplete on some file that the command doesn't expect, what I usually do is replace the command with 'ls', then autocomplete, then replace 'ls' with the command again. It may take more time, but it's worth it in dangerous situations (an excellent example of a dangerous situation : using dd).

---

### Post by nandemonai on 2009-05-19
I _think_ the default output is stdout?

```
of=FILE
              write to FILE instead of stdout
```

---

### Post by jimmy the saint on 2009-05-19
@Mornedhel: Hey thanks for the tip, I didn't even think about using a different command for the file complete.  Definitely easier than copy/paste anyway.  

@everyone: Thanks for the info on the stdout.  I'm using my mobile to ask the questions because I didn't want to do anything on the main box until I was sure what I had done!  If all that happened was gobbledygook on the screen, I can live with that as a lesson!

Thanks everyone!

---

