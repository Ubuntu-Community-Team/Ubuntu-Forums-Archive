---
title: "terminal syntax"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by squrl on 2010-10-27
If the following command works.

timidity ~/Desktop/conversion folder/xxx.mid -O -o ~/Desktop/conversion folder/xxx.wav

What would the command be to do all the mid files in that folder?

Thanks

---

### Post by CharlesA on 2010-10-27
It gets complicated with multiple files.

You could use wild cards, but I don't know if it'll work or not.

```
timidity ~/Desktop/conversion\ folder/*.mid -O -o ~/Desktop/conversion\ folder/*.wav
```

Also note: the terminal doesn't like spaces, you'd have to escape them with "\" for it to read them.

See [here]("http://www.tuxfiles.org/linuxhelp/weirdchars.html") for some more info.

---

### Post by DaithiF on 2010-10-27
caveat: i've never heard of timidity...
but generically, something like this should work:

```
#!/bin/bash
shopt -s nullglob
for file in "~/Desktop/conversion folder/"*.mid
do
   filename="${file##*/}"
   converted_filename="${filename%.mid}.wav"
   echo timidity "$file" -O -o "~/Desktop/conversion folder/$converted_filename"
done

```
save this as a script, chmod +x that script to make it executable, then run it.  remove the 'echo' prefix to the timidity line if happy it is doing the right thing.

---

