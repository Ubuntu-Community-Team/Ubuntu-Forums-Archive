---
title: "tar: Exiting with failure status due to previous errors"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by pstevenson83 on 2009-12-17
trying to install rockbox which is a tar.bz2 file... I download the installer, and type tar -jxvf rbutiqtv-1.2.3.bz2  which is the name of the file. It's says read only in the downloader so i'm sure this is probably a problem i need to address. but anyways... how do i fix the failure status. how am i supposed to ever download this if i can never be allowed to again..


BOY DO I FEEL LIKE DUMBY.... WANT TO DELETE THIS NOW..DON'T SEE A DELETE BUTTON EVEN THOUGH IT SAID EDIT/DELETE ON THE ICON..

---

### Post by pro003 on 2010-04-16
> **pstevenson83 said:**
> trying to install rockbox which is a tar.bz2 file... I download the installer, and type tar -jxvf rbutiqtv-1.2.3.bz2  which is the name of the file. It's says read only in the downloader so i'm sure this is probably a problem i need to address. but anyways... how do i fix the failure status. how am i supposed to ever download this if i can never be allowed to again..


BOY DO I FEEL LIKE DUMBY.... WANT TO DELETE THIS NOW..DON'T SEE A DELETE BUTTON EVEN THOUGH IT SAID EDIT/DELETE ON THE ICON..

first, I am well aware of the date and don't bother point that out.

second the command which you gave here tar -jxvf "nameofthefile.tar.bz2 didn't work because the file was owned by root and not you as a user and that's why you could not even delete it after.

you should add permission to a file using **chmod** or maybe **chown** and then manipulate with the file i.e extract it delete it or whatever or you could use prefix **sudo** in terminal in situations like this which gives you privilege of the root for a moment or so...

P.S. I replied on this post cause of other people who may bump into it, not because of the this dude who probably doesn't need any help anymore I guess...

:lolflag:

---

### Post by Elfy on 2010-04-16
Thanks for answering an unanswered post :) - I will close it now though.

---

