---
title: "xargs +find + Kayone =fail"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by Kayone on 2010-01-12
find . \( -name "*\?*" -o -name "*:*" -o -name "*\;*" -o -name "*\**" \) | xargs -n1 -I{} rename "\*" "" {} 
I am wondering why this isn't working. Any ideas?

I am trying to dig through some directories (under the current directory) for special characters and remove them. Realistically, I would like to replace it with a underscore but I can't seem to get anything to work. I am failing at xargs... 

I'm a noob. I am getting the following error:

syntax error at (eval 1) line 2, at EOF
xargs: rename: exited with status 255; aborted

---

### Post by sisco311 on 2010-01-12
EDIT:
[s]
```
find . \( -name "*\?*" -o -name "*:*" -o -name "*\;*" -o -name "*\**" \) -exec rename -n 's/[?:;*]/_/g' {} \;
```[/s]

```
find . -depth \( -name "*\?*" -o -name "*:*" -o -name "*\;*" -o -name "*\**" \) -execdir rename -n 's/[?:;*]/_/g' {} \;
```

---

### Post by Kayone on 2010-01-13
> **sisco311 said:**
> EDIT:
[s]
```
find . \( -name "*\?*" -o -name "*:*" -o -name "*\;*" -o -name "*\**" \) -exec rename -n 's/[?:;*]/_/g' {} \;
```[/s]

```
find . -depth \( -name "*\?*" -o -name "*:*" -o -name "*\;*" -o -name "*\**" \) -execdir rename -n 's/[?:;*]/_/g' {} \;
```

1. Will I need to sudo to run exec? I run it and it says things are renamed yet they aren't actually renamed. If I run it again, it says the same things are renamed but nothing is...

2. It appears this works on file names only. Is that correct? 

Thanks sisco!

---

### Post by sisco311 on 2010-01-13
> **Kayone said:**
> 1. Will I need to sudo to run exec? I run it and it says things are renamed yet they aren't actually renamed. If I run it again, it says the same things are renamed but nothing is...

2. It appears this works on file names only. Is that correct? 

Thanks sisco!

To actually rename the files you have to remove the -n option from the rename command.

It works with directories too, that's why you need the -depth (*process each directory's contents before the  directory  itself.*)and -execdir (*run the command from the subdirectory containing the matched file*) options (see *man find* for details), otherwise rename will try to rename i.e. ./dir?name/file;name to ./dir_name/file_name witch throws a no such directory errors.

---

### Post by Kayone on 2010-02-04
I was able to get rid of "a lot" of the whitespace and removing all special characters. Now I am having issues with "the rest" of the whitespace.

Some of the file/directory names have leading and trailing white space that didn't delete with the rest of it. Some of the files have multiple white spaces in the middle of the files. The thing I am wondering (outside of finding a solution), could this be because I copied and pasted the file names from a different source. Could it be formatting tags (like line breaks) that keeps these files from renaming?

---

### Post by Kayone on 2010-02-09
> **Kayone said:**
> I was able to get rid of "a lot" of the whitespace and removing all special characters. Now I am having issues with "the rest" of the whitespace.

Some of the file/directory names have leading and trailing white space that didn't delete with the rest of it. Some of the files have multiple white spaces in the middle of the files. The thing I am wondering (outside of finding a solution), could this be because I copied and pasted the file names from a different source. Could it be formatting tags (like line breaks) that keeps these files from renaming?

I gave up and did it manually. I fought the bash and the bash won :(

Thanks goes out to everyone that tried to help or thought about it.  You may not have solved my problem but you made the manual renaming a hell of a lot faster!!

New problems OTW.

---

### Post by Paddy Landau on 2010-02-09
For mass renaming, you might like pyrenamer. You can find it in the normal repositories.

---

### Post by Kayone on 2010-02-09
> **Paddy Landau said:**
> For mass renaming, you might like pyrenamer. You can find it in the normal repositories.

Haha. I figured there would be something written for it. I am really trying to learn bash though. 

I am going to grab it now. It know my replacement (at my current location) is going to need it.

---

