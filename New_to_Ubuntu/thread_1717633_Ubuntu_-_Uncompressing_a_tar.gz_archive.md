---
title: "Ubuntu - Uncompressing a tar.gz archive"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by euloiix on 2011-03-30
Hi everyone, 

I am trying to uncompress a tar.gz archive. 
The file is on my Desktop and this is what I do: 

[HTML]sudo tar -zxf Desktop/flashplayer_10_2r153_1_linux.tar.gz [/HTML]

Unfortunately nothing is happening. The archive is not decompressed on my Desktop. Any guess of what I did wrong ? 

Thank you in advance :P

---

### Post by coffeecat on 2011-03-30
1 - Don't use sudo.

2 - Are you sure you've got the filename correct? Do you get any terminal errors?

3 - If you want to keep it simple, double-click on the tarball  and then click on "extract".

---

### Post by euloiix on 2011-03-30
Ok I have done it graphically and it worked alright.
Thanks for this by the way.

But still I woudl love to understand why it was not working.
With or without "sudo" did not change the result, and the terminal was not returning anything after the command.

And I am sure the name was the right one, as the terminal wrote it for me.

Any other guesses ??

---

### Post by nothingspecial on 2011-03-30
It did work, it's in your home folder.

tar will extract the archive to your current working directory.

If you had done
```

cd Desktop
tar -zxf flashplayer_10_2r153_1_linux.tar.gz
```

Then it would have extracted it to your Desktop.

When the terminal gives no output it means what you've tried to do worked. It only tells you if you did it wrong.

If you use the -v flag with tar next time it will tell you what it's doing

```
tar -zxvf 
```

---

### Post by euloiix on 2011-03-30
Atcha !!! 

This is what I needed ! Thank you. Now I will know ! tar is extracting in the current working directory, not in the archive directory as I assumed (I do not know why :) ).

And I will use the verbose option next time also.

Thanks again.

---

### Post by Tmcarr on 2011-03-30
Yea, when you ran it as root (you used sudo) it unpacked it into roots homedir.

---

