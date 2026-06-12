---
title: "Recursively copy only jpg's"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by japhyr on 2010-04-04
Hello,

I have a backup directory on an external hard drive with thousands of folders and thousands (probably hundreds of thousands) of files.  The directory is the result of recovering files from a computer after an accidental deletion of all image files.

I want to copy all the image files from this directory to one folder, so I can then sort through those files and see what to keep.  I don't know whether to use cp or rsync, and which options to specify to do this right.  I also want to make sure this is efficient, since there are so many files to work with.  I know it should be something like:
```
sudo cp -r *.jpg /source_dir /dest_dir
```
or
```
sudo rsync *.jpg /source_dir /dest_dir
```

Can someone help me figure out what this command should be, exactly?

Also, should I do this with the external drive connected, or would it be significantly easier to copy the source directory to my hard drive, do the copying locally, and copy the results back to the hard drive?  It is about 40G of data, and the drives are both 500G with over 400G of empty space on each.

---

### Post by NightwishFan on 2010-04-04
Edit: Oddly this command does work, I advise rsync then.

---

### Post by lisati on 2010-04-04
If you're using cp, I'd suggest something like this:
```

cd /source_dir
sudo cp -r *.jpg /dest_dir

```
It would be possible to use mv instead of cp, but cp has the advantage of keeping the original available if something goes wrong with the copy.

---

### Post by NightwishFan on 2010-04-04
I had just tried a similar command using cp and it did not work for recursive directories. Could you help me debug it?
```
cd /directory/of/jpgs
cp -r -t */dest/dir* \*.JPG
```

---

### Post by japhyr on 2010-04-04
I just made a test directory with two folders of jpg's in it, to try out my command.  I tried:
```
sudo cp -r *.jpg ~/Desktop/test_recovery/recovered_all ~/Desktop/test_recovery/recovered_jpgs
```
I got an error message:
```
cp: cannot stat `*.jpg': No such file or directory
```

But, it copied all the jpg's in the test directories to the desired directory.  Can I safely ignore this error?
Edit:  I just added a .txt file to one of the source directories, and it copied the txt file to the destination.  So, the command does not work.

---

### Post by NightwishFan on 2010-04-04
I get the same error. Press alt+f2 type:
```
gnome-search-tool
```

Search for ,jpg files there.

---

### Post by japhyr on 2010-04-04
This rsync command
```
rsync -a --include "*/" --include "*.jpg" --exclude "*" source_dir/ dest_dir/
```
works.  I got it [here]("http://maururu.net/2007/rsync-only-files-matching-pattern/comment-page-1/").

However, it copies the file structure as well, and that is not good because there will still be a couple thousand folders to look through.  I want to somehow be able to only copy the jpg files that are found, but not the file structure.  But then there might be a lot of conflicting file names.  Maybe that's why others write scripts to deal with directories of this size.

---

### Post by SnickerSnack on 2010-04-04
I think there is no trivial way to do what your asking because it would likely result in the collision of file names, one file would get over written by one with another name.  Edit: Oh yeah, you knew that...

You'll probably have to write a shell script (or perhaps python or perl) to rename the files as they're copied.  Edit: that too...

---

### Post by EssexEagle on 2010-04-04
> **japhyr said:**
> I just made a test directory with two folders of jpg's in it, to try out my command.  I tried:
```
sudo cp -r *.jpg ~/Desktop/test_recovery/recovered_all ~/Desktop/test_recovery/recovered_jpgs
```
I got an error message:
```
cp: cannot stat `*.jpg': No such file or directory
```

But, it copied all the jpg's in the test directories to the desired directory.  Can I safely ignore this error?
Edit:  I just added a .txt file to one of the source directories, and it copied the txt file to the destination.  So, the command does not work.

The cp command requires the syntax
```
cp *files_to_copy* *destination_to_copy_to*
```

You're trying to do
```
cp  *files_to_copy*  *directory_to_copy_from*  *destination_to_copy_to*
```

You don't need to specify the files and the directory they're in separately like that.  The shell is interpreting your command as copy all *jpg*'s from the directory you happen to be in at the time, plus **everything** from *~/Desktop/test_recovery/recovered_all* (which is why it's getting the .txt files as well) into *~/Desktop/test_recovery/recovered_jpgs*

As suggested by lisati, cd into *~/Desktop/test_recovery/recovered_all* first and then run
```
sudo cp -r *.jpg  ~/Desktop/test_recovery/recovered_jpgs
```



*Edit:* As discussed above, this will cause problems if you have files in separate subdirectories under *~/Desktop/test_recovery/recovered_all* with the same name.  But I have at least explained to you why your cp command wasn't working ;)

---

