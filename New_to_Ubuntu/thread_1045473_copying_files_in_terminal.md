---
title: "copying files in terminal"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by JustinJS on 2009-01-20
What I am trying to do is extract all mine mp3 files that are in subfolders into one main folder. Can anyone help me i cannot remember how to do this in terminal

---

### Post by mali2297 on 2009-01-20
Say that you want to copy the mp3 files in 'subfolder1' and 'subfolder2' to 'destinationfolder'. Then type 
```

cp subfolder1/*.mp3 subfolder2/*.mp3 destinationfolder

```
If you want to see what cp does, use the -v flag, like
```

cp -v subfolder1/*.mp3 subfolder2/*.mp3 destinationfolder

```

---

### Post by sisco311 on 2009-01-20
> **JustinJS said:**
> What I am trying to do is extract all mine mp3 files that are in subfolders into one main folder. Can anyone help me i cannot remember how to do this in terminal

```
find /path/to/mp3s -name "*.mp3" -exec cp {} /path/to/destination/dir \;
```

---

### Post by RequinB4 on 2009-01-20
> **sisco311 said:**
> ```
find /path/to/mp3s -name "*.mp3" -exec cp {} /path/to/destination/dir \;
```

Is find recursive?

Edit: cp has a recursive option (-R) so i'm not sure the usefulness of using this command over ```
cp -R *.mp3 /destination/folder
```

---

### Post by donkyhotay on 2009-01-20
'cp' is the command you want to use to copy in the CLI. If you are ever uncertain on how to use a specific command you can read the manual by typing 'man' then the command name. For example
```
man cp
```
will give you information on using the cp command. Very useful when you can't remember things like 'whats the option to copy folder recursively?' and other things like that.

---

### Post by sisco311 on 2009-01-20
> **RequinB4 said:**
> Is find recursive?

Yes.

*find /path/to/mp3 -name "*.mp3"* = find all *.mp3 in /path/to/mp3 and sub-folders

*-exec cp {} /path/to/destination/dir \;* = copy the files to /path/to/destination/dir

e.g.

```
find ~/music -name "*.mp3" -exec cp {} ~/allmp3 \;
```

```

~/music/0.mp3
~/music/band1/1.mp3
~/music/band1/2.mp3
~/music/band2/album1/3.mp3
~/music/band2/album1/4.mp3
~/music/band2/album2/5.mp3
~/music/band2/album2/6.mp3

```

-->

```

~/allmp3/0.mp3
~/allmp3/1.mp3
~/allmp3/2.mp3
~/allmp3/3.mp3
~/allmp3/4.mp3
~/allmp3/5.mp3
~/allmp3/6.mp3

```

---

### Post by snova on 2009-01-20
> **RequinB4 said:**
> Edit: cp has a recursive option (-R) so i'm not sure the usefulness of using this command over ```
cp -R *.mp3 /destination/folder
```

No, because globbing is done by the shell (cp never sees '*.mp3', it gets a list of files). -R just makes it copy subdirectories.

---

