---
title: "Weird file names"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by smitty96 on 2010-03-25
After using mdf2iso to convert an mdf to an iso file, all the files inside the iso have ";1" at the end of the name. After extracting the files, is there a way to remove that from all the files in the directories and subdirectories? I really have no idea why it's there... Please help me!

---

### Post by srs5694 on 2010-03-25
Those extensions are part of the ISO-9660 filename standard. Linux normally hides them from you. I'm not familiar with the mdf2iso utility or whatever it converts from, so I don't know what it might be doing or why the resulting files are treated differently. You might want to check the mdf2iso documentation to see if it's got an options that might be relevant, though. Look for anything that references filename creation options and options to create or not create Joliet or Rock Ridge extensions, and play with those options. It's also conceivable that a Linux mount option would have an effect. Type "man mount" and then search for iso9660 options. (In the usual manpage reader, typing "/" followed by a search term searches, so type "/iso9660" and hit Enter. The main section on this option isn't the first hit, though, so type "/" and Enter to search again.)

If you can't find anything relevant in your conversion or mount options, you could use a simple shell script to rename the files; however, my familiarity with the commands you'd need is a bit less than necessary for me to crank out such a script in a minute or two, so I'm afraid I'll have to leave it at that.

---

### Post by kaibob on 2010-03-25
The following command will rename the files and acts recursively. You need to change /target/directory to whatever is applicable. The -n option directs rename to do a dry run and report proposed changes. If all looks OK, change -n to -v to actually rename the files.

```
find /target/directory -type f -exec rename -n 's/;1$//' '{}' ';'
```

---

### Post by smitty96 on 2010-03-27
Thanks guys. Unfortunately, the program on that disc backup didn't run. But I did manage to find my original disc, so hopefully that'll work better.

---

