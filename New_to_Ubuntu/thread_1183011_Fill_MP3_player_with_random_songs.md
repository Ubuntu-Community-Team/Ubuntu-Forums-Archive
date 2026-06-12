---
title: "Fill MP3 player with random songs"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by Commander_Bob on 2009-06-09
I have a Sansa Fuze, which shows up as two USB drives, 8.2GB internal memory and my 2GB microSD card.

I can simply copy the music to the drive and play it later, however I have more music than it can hold. I need a way to fill  the player and card with random songs, without repeats. Would this be possible with a script or an existing program? 

Thanks,
Justin Rajewski

---

### Post by spiceminesofkessel on 2009-06-09
A good scripting language, such as [Python]("http://www.python.org"), should be able to handle a task such as this. I personally don't know of a specific script to do the chore, but you essentially need to do the following in a script.

[LIST=1]
[*]Read the directory containing the pool of mp3's
[*]Assign an indexing value for each mp3
[*]Use a random number script to choose an mp3
[*]Copy the mp3 to the mp3 player
[*]Repeat steps 3 and 4 a given number of times
[/LIST]
I know Python can do such a chore, because I wrote a backup script in Python which accesses files to back up, deletes the files in the destination directory, copies them to the destination directory, and logs each action.

Python is great because you can get the language and a great guide for free.

---

### Post by aysiu on 2009-06-09
This may help you. I haven't tried it out myself, so I don't know: [Script to tramsfer random songs to portable media device](http://ubuntuforums.org/showthread.php?p=774344#post774344)

---

### Post by Commander_Bob on 2009-06-09
Thanks for that!

I modified it a bit, it now fills up one device then once it is full the other. I also made it print the current song it is copying and what total percentage it has completed.

I also fixed a bug where if the path of the device was /media/disk grep would return /media/disk and /media/disk-1. To do that I added -x to int/ext_player_is_mounted() and made it '/media/disk ' (added space) to the int/ext_get_free_space().

I haven't fully tested it yet, it is running right now, so it I find any problems I'll fix them.

Here it is ```
#!/usr/bin/env python

import sys, os, random

src_path = "/home/justin/Music/All"
int_dev_path = "/media/disk-1"
int_dest_path = int_dev_path + "/MUSIC"
ext_dev_path = "/media/disk"
ext_dest_path = ext_dev_path + "/MUSIC"

# when the player only has 3 megs left, we'll stop trying to copy
# you can lower this to 0 (or anything) so it will try to fit every
# song in your collection, but consider the player might have 2 bytes
# left and you have 800000 songs
player_is_almost_full = 3000000

# returns whether or not int_dev_path is mounted
def int_player_is_mounted() :
    return (os.popen("mount | awk '{print $3}' | grep -x " + \
                        int_dev_path).read().replace("\n", "") == int_dev_path)

# returns the # of bytes avail on the player
def int_get_free_space() :
    return int(os.popen("df -B 1 | grep `mount | grep '" + int_dev_path + \
                            " ' | awk '{print $1}'`" + " | awk '{print $4}'") \
                            .read().replace("\n", ""))

# returns whether or not int_dev_path is mounted
def ext_player_is_mounted() :
    return (os.popen("mount | awk '{print $3}' | grep -x " + \
                        ext_dev_path).read().replace("\n", "") == ext_dev_path)

# returns the # of bytes avail on the player
def ext_get_free_space() :
    return int(os.popen("df -B 1 | grep `mount | grep '" + ext_dev_path + \
                            " ' | awk '{print $1}'`" + " | awk '{print $4}'") \
                            .read().replace("\n", ""))

# returns the # of bytes of a given file name
def get_file_size(file_name) :
    return int(os.popen("ls -l \"" + file_name + "\" | awk '{print  $5}'") \
                            .read().replace("\n", ""))

if __name__ == "__main__" :
    if (not (int_player_is_mounted() and ext_player_is_mounted())) :
        print "Your mp3 player needs to be mounted on " + int_dev_path + \
                 " and " + ext_dev_path + " before you can write to it."
        sys.exit()

    os.popen("mkdir -p " + int_dest_path)
    os.popen("mkdir -p " + ext_dest_path)

    # find our entire music collection, if it's very large this could be bad
    # it works ok over here
    file_list = os.popen("find -L \"" + src_path + \
                            "\" -type f -iname \"*.mp3\" -o -iname \"*.ogg\"") \
                            .read().split("\n")[0:-1]

    start_free_space = int_get_free_space() + ext_get_free_space()

    # loop until there are no more files to copy
    # if the device gets close to full we will stop too
    while (len(file_list) > 0) : #{
        # see how much the player can fit
        int_free_space = int_get_free_space()
	ext_free_space = ext_get_free_space()

        print "Copied " + '%.2f'%(((float(start_free_space) - \
               (int_free_space + ext_free_space)) / start_free_space) * 100) + "%"

        if (int_free_space < player_is_almost_full and \
            ext_free_space < player_is_almost_full) :
            break       # can't really fit anything else

        # choose a random file number
        index = random.randint(0, len(file_list) - 1)

         # quotes in the file name will F everything up
        file_list[index].replace("\"", "\\\"")

        # see if it will fit on the player and copy it if so
        if (int_free_space > get_file_size(file_list[index])) :
            print "Copying " + os.path.basename(file_list[index]) + " to " + int_dest_path
            os.popen("cp \"" + file_list[index] + "\" " + int_dest_path)

	elif (ext_free_space > get_file_size(file_list[index])) :
            print "Copying " + os.path.basename(file_list[index]) + " to " + ext_dest_path
            os.popen("cp \"" + file_list[index] + "\" " + ext_dest_path)

        # put the last file in our list where the one we just copied was
        # if it's the last file, we'll just toss it
        if (index != len(file_list) - 1) : #{
            file_list[index] = file_list.pop(len(file_list) - 1)

        else :
            file_list.pop(len(file_list) - 1)
```

---

