---
title: "recording music streams + &quot;tee&quot; command, ugly filenames"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by Stigmata13 on 2010-12-14
Hello. I've recently started using shell-based radio client, and by using some of the internal functions of the config, it is able to "record" the tracks by passing the stream to "tee", which then writes them to the disk, while also playing it with madplay so you can listen at the same time.

As stated in the programs manual, the program says that during this export it supports format strings, for example:

```
tee "/home/user/someplace/%a - %t.mp3" | madplay -Q -
```the **%a** would use the artist name, and the **%t** would use the track title, and it ***should ***give you a file with a name such as:

**artist - track.mp3**

However, for some reason I can't get this to work for the life of me. If the artist and the track are both a single word, it comes out fine. But if the artist/track names have more than one part, the output filename always ends up like this:

**artist\ name - track\ name\ here.mp3**

Where instead of just spaces, there is a **"\"** followed by the space.
This can get quite annoying, as i have to go in an manually fix the file names.

Does anyone have any idea what could be causing this problem, or a fix for it? Is it a bug in the main program, exporting the format strings to "tee," or is "tee" doing it itself? Help would be very appreciated. Trying to figure out this problem has been a real learning experience; although however hard I look I can't seem to find a fix anywhere.

Edit: Forgot to mention it also likes to add the **"\"** right before apostrophes, for example:

**artist\'s\ name - song\'s\ title.mp3**

---

### Post by Vaphell on 2010-12-14
and what happens when you remove quotes from tee part (don't forget to escape spaces if needed)?
try
```
tee /home/user/someplace/%a\ -\ %t.mp3
```

these \ are there to escape spaces and other stuff meaningful from command parsing perspective. Spaces delimit parameters, ' and " are used to enclose strings

cmd a b.txt => cmd 'a' 'b.txt' - 2 different parameters, command fails
you either have to escape the spaces so the command ignores them and treats as an ordinary character
cmd a\ b.txt - space becomes invisible
or to put the name in ""
cmd "a b.txt" - space is inside the quotes, so it's invisible

apparently your one liner does both, so you get escaped sequence in quotes which is too much of the good.

---

### Post by Stigmata13 on 2010-12-14
> **Vaphell said:**
> and what happens when you remove quotes from tee part (don't forget to escape spaces if needed)?.

Oh wow, I guess sometimes you just learn some things the hard way.
Thanks, that did the trick. After removing the quotes and adding escape spaces, this one finally worked:

```

tee /home/user/someplace/%a\ -\ %t.mp3 | madplay -Q -
```

Thanks a bunch :D

---

