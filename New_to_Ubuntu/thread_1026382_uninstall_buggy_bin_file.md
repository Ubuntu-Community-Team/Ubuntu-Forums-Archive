---
title: "uninstall buggy bin file"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by bsowers on 2008-12-31
Hello all

I was trying to read a syllabus which seemed to be in a bin file when I downloaded it, so I looked at directions of how to install bin files so I could read it. I did chmod 755 filename and then ran it.

Now my home directory, where it's installed, will not open (I can navigate to my file system but not to my home directory. I tried the following to remove it: ```
brandon@balius:~$ locate cri200b
/home/brandon/cri200b.09.syl
/home/brandon/.local/share/Trash/files/cri200b.09(2).syl
/home/brandon/.local/share/Trash/files/cri200b.09(3).syl
/home/brandon/.local/share/Trash/info/cri200b.09(2).syl.trashinfo
/home/brandon/.local/share/Trash/info/cri200b.09(3).syl.trashinfo
brandon@balius:~$ rm -r cri200b.09.syl
rm: cannot remove `cri200b.09.syl': No such file or directory

```

---

### Post by jrusso2 on 2008-12-31
A link to this file might prove helpful.

---

### Post by Michael.Godawski on 2008-12-31
hi,

can you please post the exact code how you changed the permissions?

It should be somewhere in

```
less ~/.bash_history
```

And be cautious with the rm command please; always give the full path to the file you want delete.

---

### Post by bsowers on 2008-12-31
the link to the file is here: [URL="http://classes.ucdavis.edu/search/reader.cfm?term=200901&crn=27860&pid=2"]http://classes.ucdavis.edu/search/reader.cfm?term=200901&crn=27860&pid=2
[/URL]

The commands i used to change permissions and run the files are these, according to bash_history:```
chmod 755 cri200b.09.syl
sudo ./cri200b.09.syl

```

---

### Post by bsowers on 2008-12-31
Does anyone have any ideas? If I can't figure anything out, I might do a re-install.

---

