---
title: "Command to copy files in subfolders to one folder"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by humphreybc on 2010-01-20
Okay so I have a bunch of images set up like this:

- Images
-- Folder 1
-- Folder 2
-- Folder 3
... etc

In each folder there are a tonne of images. I want to be able to copy all the images in each folder into a folder called "all" so that I can activate a slideshow using gThumb with ALL my images, instead of just one folder.

I could open each folder manually and copy everything, then paste into the "all" folder, then repeat. But this is time consuming, and there must be a command line way :)

---

### Post by nothingspecial on 2010-01-20
```
cd Images
```

That is get into the parent directory, the one you want all your images in.

```
find ./ -name '*.jpg' -exec cp '{}' ./ \;
```

This assumes all the images end with the .jpg file extention.

If there are only images in all the sudirectories, but they have different file extensions .png .JPG .jpg .jpeg etc then

[COLOR="Red"][SIZE="4"]Do not do this in your home directory or you will have a right mess on your hands
[/SIZE][/COLOR]

                              [SIZE="3"][COLOR="Red"]|
                              |
                              |
                              V[/COLOR][/SIZE]   
```
find ./ -type f -exec cp '{}' ./ \;
```
 will move any file in all the subdirectories to the one you`re in.

You can then rename the parent folder "all" 
Alternatively use feh to create the slideshow.

```
sudo apt-get install feh
```

Then ```
feh -Fzr -D 5 ~/Images
```

This will create a slideshow. F is fullscreen, z is random, r tells feh to go through the directories recursively and D specifies the time each picture is displayed before changing to the next one. The time is in seconds so my example would delay the pictures for 5 seconds.

I am known for making typos, test the code first.

---

### Post by a2z on 2010-01-20
> **humphreybc said:**
> Okay so I have a bunch of images set up like this:

- Images
-- Folder 1
-- Folder 2
-- Folder 3
... etc

In each folder there are a tonne of images. I want to be able to copy all the images in each folder into a folder called "all" so that I can activate a slideshow using gThumb with ALL my images, instead of just one folder.

I could open each folder manually and copy everything, then paste into the "all" folder, then repeat. But this is time consuming, and there must be a command line way :)

I've managed to figure out how to move folders with a command to another drive. 
My first recommendation is to open the help menu and search "command line"
It helps guide for other commands you may need at any given time.

If your folder name has a space, you have to substitute it with * . Meaning DON'T use spaces when dealing with folders.

Also note, you have to use -r or maybe -R prior to your folder name being moved.  such as.... sudo mv -r your*folder*name /yournewdirectory.

Hope this helps.

a2z

---

### Post by Azteka on 2010-01-20
```
cp /images/{folder1,folder2,etc}/* /images/all/
```

---

### Post by mikechant on 2010-01-20
This post 
[http://ubuntuforums.org/showpost.php?p=4547268&postcount=4](http://ubuntuforums.org/showpost.php?p=4547268&postcount=4)
shows a command to merge all subfolders into the current folder. 
If you use 'cp' instead of 'mv' and change the '.' to the location of your 'all' folder this should work. One issue is if you place your 'all' folder under 'images' this could cause problems.


The folowing command should work if you are in the Images folder and the 'all' folder is *not* under the Images folder:
```
find . -type f -exec cp '{}' /path/to/all/folder \;
```

I think the following might work if the 'all' folder *is* in the images folder by excluding the 'all' folder from the find:
```
find . -type f -wholename './all' -prune -exec cp '{}' ./all \;
```
Again your current directory (folder) should be set to Images

Warning: I'm typing this with access to the 'find' command manual but without a Linux system to test on,  so I suggest you make a copy of your images file and test this on the copy.
Also note you can test the 'find' part of the command by replacing the '-exec blah blah' with '-print', as mentioned in the post referenced above - this will just give you a list of files selected by find.

---

### Post by anaconda on 2010-01-20
> **nothingspecial said:**
> 

```
find ./ -name '*.jpg' -exec mv '{}' ./ \;
```

T.

I think the OP wanted to copy the files, and not move them. So you should replace the mv to cp in the above.

---

### Post by nothingspecial on 2010-01-20
> **anaconda said:**
> I think the OP wanted to copy the files, and not move them. So you should replace the mv to cp in the above.

oops - corrected

---

### Post by airtonix on 2010-01-20
> **a2z said:**
> 
If your folder name has a space, you have to substitute it with * . Meaning DON'T use spaces when dealing with folders.

Sorry I think you are mistaken.

---

### Post by a2z on 2010-01-20
> **airtonix said:**
> Sorry I think you are mistaken.

I've moved all my folders from cd's to my 500g hd. This is the only way it worked. So I guess believe what you wish. I know what worked for me hehehe

---

### Post by doas777 on 2010-01-20
looks like you already have some good answers to the query, but figured I'd chime in as well. here is my python script for almost the same thing. it walks all subdirs in a dir, and causes all the files within them to erupt into the base dir. 

```

#!/usr/bin/env python
#usage: volcano.py <basedirpath>

import os, sys, shutil


def main():
    for a in sys.argv:
        arg = os.path.normpath(a)
        for root, dirs, files in os.walk(arg, False):
            for f in files:
                src = os.path.join(root, f)
                fname =  os.path.split(src)[1]
                try:
                    shutil.move(src, os.path.join(arg, fname))
                    print "moved %s to %s" %(src, os.path.join(arg, fname))
                except Exception, e:
                    print "Errpr moving file %s to %s" %(src, os.path.join(arg, fname))
                    print "Exception: ", e 

if __name__ == "__main__":
    main()

```

---

### Post by falconindy on 2010-01-20
> **a2z said:**
> I've moved all my folders from cd's to my 500g hd. This is the only way it worked. So I guess believe what you wish. I know what worked for me hehehe
While globbing is a solution, it's not the only solution. You can escape white space (and other problematic characters) with backslashes, or quote the path names... e.g.:

```
Copy "This dir has spaces/in it/" anotherdir/
```
or
```
Copy This\ dir\ has\ spaces/in\ it/ anotherdir/
```
Note that you cannot use brace expansion if you choose to quote your paths.

@OP: If you're doing this purely for organization purposes, use hard links instead of a real copy. Also...

```
cp -l "./Images/*/*" ./newfolder-wit-all-dem
```

---

### Post by airtonix on 2010-02-03
> **a2z said:**
> I've moved all my folders from cd's to my 500g hd. This is the only way it worked. So I guess believe what you wish. I know what worked for me hehehe

As the above poster has outlined, wildcards may have worked for you in that particular case... but I would not guarantee that it would work in every single case...

The safe way to deal with spaces in a file or folder name is to escape them with a forward slash.

"File\ Name"

not "File*Name", which will match : 

"File1MyName"
"FileNotMyName"
"FileOMGTHISISROOTName"

Using wildcards has unpredictable consequences.

It certainly has its uses, specially with moving files/folders with a distinct naming pattern.

---

### Post by chewearn on 2010-02-03
> **humphreybc said:**
> Okay so I have a bunch of images set up like this:

- Images
-- Folder 1
-- Folder 2
-- Folder 3
... etc

In each folder there are a tonne of images. I want to be able to copy all the images in each folder into a folder called "all" so that I can activate a slideshow using gThumb with ALL my images, instead of just one folder.

I could open each folder manually and copy everything, then paste into the "all" folder, then repeat. But this is time consuming, and there must be a command line way :)

Rather than copying loads of photos into one directory, here is a solution that doesn't require any copying.

```
FILELIST=(); while read FILE ; do FILELIST+=( "$FILE" ); done < <(find -type f); gthumb -s "${FILELIST[@]}" &
```

---

### Post by Anvarlaksh on 2012-01-02
Am an absolute noob myself.  I chanced upon a quick way of doing this.  Use an archive tool to "zip" all the folders into the folder where you want the individual files.  Then "unzip" them using the same tool - this time however, uncheck the "recreate sub directories" option.  This method seems to work just fine for me.  Not sure if this is what you were looking to do.

---

### Post by oldos2er on 2012-01-02
Closed, necromancy.

---

