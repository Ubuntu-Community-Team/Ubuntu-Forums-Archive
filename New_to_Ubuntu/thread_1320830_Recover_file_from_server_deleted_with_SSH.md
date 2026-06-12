---
title: "Recover file from server deleted with SSH"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by RichardCL on 2009-11-09
Hi Forum,

I just deleted a directory on my server using SSH through nautilus. The server is only accessible through putty and ssh. Although I used Nautilus to delete the files, they aren't mentioned in the trash, presumably because the trash is on my local computer.

Any way to access trash on the remote computer?

TIA


Rich

---

### Post by doas777 on 2009-11-09
photorec may do it, if the files were of a known parsable type.

---

### Post by dvlchd3 on 2009-11-09
Either by command line on remote machine:

```

cd ~/.local/share/Trash/files
ls

```

Of if you show hidden files in Nautilus (Ctrl+h) browse to
/home/[username]/.local/share/Trash/files

This is the location of everything that is in the "trash"

---

### Post by RichardCL on 2009-11-09
> **dvlchd3 said:**
> Either by command line on remote machine:

```

cd ~/.local/share/Trash/files
ls

```

Of if you show hidden files in Nautilus (Ctrl+h) browse to
/home/[username]/.local/share/Trash/files

This is the location of everything that is in the "trash"

I've not managed to find a directory called .local in the home folder. I did find a folder called lost+found but it appears to be empty.

I've installed photorec and it is doing some recovery for the next 3 hours. Hopefully that will turn up something. Since photorec is creating a lot of data I hope it isn't recording over my files.

Thanks for the help so far.

---

