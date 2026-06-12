---
title: "Need help installing a patch"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by Shintrick on 2009-05-16
I've been using Easytag to write metadata to my music files and it's been great except that there is no way to edit the 'album artist' field. I was able to get a patch that someone made which would remedy this issue, but unfortunately I'm too much of a noob to understand what to do with it.

Could someone let me know how I would integrate this patch into Easytag? Based on what I've read it seems to involve using the source code but I wouldn't know where to start.

I'm running 32-bit Jaunty if that makes a difference.

Thanks

---

### Post by XCan on 2009-05-16
What kind of patch is it? Was it only supplied to you through a .diff file, or is it the complete source code for the affected file? .diff files contains the changes made to a source code which you can apply into your bugged source code. Of course, after patching the code, you would need to compile it. I'm not an expert on this matter, so I think I better leave the details for someone else.

---

### Post by Shintrick on 2009-05-17
Yes its a .diff file. I unpacked it and it's just sitting there. Just not sure how to use it to alter the source code.

---

### Post by charliehorse55 on 2009-05-17
You will need to download the source. 

Then cd into the directory of the unpacked source, and run 

```

patch *pathto .diff file*

```

After that is complete, 

```

make
make install

```

Done

If that was too techy, post back, and I will write more detailed instructions.

---

### Post by Shintrick on 2009-05-18
So get the EasyTag tarball, which is the source right? No problem.

> Then cd into the directory of the unpacked source, and run

Not exactly sure what that means. I can open Terminal and paste the commands you gave me, but don't know what 'cd into directory' means.

Sorry - thanks

---

