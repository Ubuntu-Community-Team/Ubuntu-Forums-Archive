---
title: "Is there something that could?"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-06-04
Is there a program or script which would open a playlist file and then copy all the songs in the playlist to a separate folder?

---

### Post by Mornedhel on 2009-06-04
Not that I know, but since .m3u files are a simple newline-separated list of relative or absolute filenames, it's probably a bash one-liner.

---

### Post by kamitsukai on 2009-06-04
> **Mornedhel said:**
> Not that I know, but since .m3u files are a simple newline-separated list of relative or absolute filenames, it's probably a bash one-liner.

would be nice;) unfortunately I will have to wait for the kindness of someone with spare time on there hands:D

---

### Post by Mornedhel on 2009-06-04
Ahem.

Carefully try the following :

```
cat playlist.m3u | xargs -d "\n" -I '{}' cp '{}' final/destination/directory
```

Replace playlist.m3u with your playlist, and final/destination/directory by the path to the directory you wish to move the files to. I've tested it with an absolute path style playlist. It should also work with relative path style playlists if you execute the command while you are in the playlist's directory.

Please make a backup before you try anything, I'd hate for my somewhat insufficient bash skills to ruin your music collection.

---

### Post by kpkeerthi on 2009-06-04
OK. I was bored and came up with a near complete version.

[B]EDIT: The below code is an illustration of concept only. For a working script, see [Post# 10]("http://ubuntuforums.org/showpost.php?p=7399190&postcount=10")
[/B]```

print_usage() {
        echo "Usage: $0 -p playlist-file -t target-folder"
        echo
        echo "Example: "
        echo "$0 -p myplaylist.m3u -t ./Music/Playlist/Files"
        echo
}

playlist=
target=

while getopts ":p:t:" opt; do
        case $opt in
                p )
                        playlist=$OPTARG
                        ;;
                t )
                        target=$OPTARG
                        ;;
                \? )
                        print_usage
                        exit 1
                        ;;
        esac
done

if [ -z $playlist ] || [ -z $target ]; then
        print_usage
        exit 1
fi

{
        echo -n "Copying"
        while read file; do
                if [ -e $file ]; then
                        echo -n "."
                        cp $file $target
                fi
        done
        echo " done"
} < $playlist

exit 0

```

```
./plcp -p myplaylist.m3u -t ./music/playlist/copied
```
The script parses each line from the playlist file (myplaylist.m3u), checks if a line is a valid file and then copies it over to the target folder (./music/playlist/copied) specified.

---

### Post by kamitsukai on 2009-06-04
> OK. I was bored and came up with a near complete version.

Code:

print_usage() {
        echo "Usage: $0 -p playlist-file -t target-folder"
        echo
        echo "Example: "
        echo "$0 -p myplaylist.m3u -t ./Music/Playlist/Files"
        echo
}

playlist=
target=

while getopts ":p:t:" opt; do
        case $opt in
                p )
                        playlist=$OPTARG
                        ;;
                t )
                        target=$OPTARG
                        ;;
                \? )
                        print_usage
                        exit 1
                        ;;
        esac
done

if [ -z $playlist ] || [ -z $target ]; then
        print_usage
        exit 1
fi

{
        echo -n "Copying"
        while read file; do
                if [ -e $file ]; then
                        echo -n "."
                        cp $file $target
                fi
        done
        echo " done"
} < $playlist

exit 0

Save this as plcp (Playlist copy!). Set execute permission. Then, run as
Code:

./plcp -p myplaylist.m3u -t ./music/playlist/copied

The script parses each line from the playlist file (myplaylist.m3u), checks if a line is a valid file and then copies it over to the target folder (./music/playlist/copied) specified.

This gives me the same error: acouple of hundred times...=[

```
carl@carl-desktop ~ $
Copying./.plcp: line 35: [: too many arguments

```

---

### Post by kamitsukai on 2009-06-04
> **Mornedhel said:**
> Ahem.

Carefully try the following :

```
cat playlist.m3u | xargs -d "\n" -I '{}' cp '{}' final/destination/directory
```

Replace playlist.m3u with your playlist, and final/destination/directory by the path to the directory you wish to move the files to. I've tested it with an absolute path style playlist. It should also work with relative path style playlists if you execute the command while you are in the playlist's directory.

Please make a backup before you try anything, I'd hate for my somewhat insufficient bash skills to ruin your music collection.

This gives me the error:

```
cat Favourites.m3u | xargs -d "\n" -I '{}' /home/carl/Desktop/folder
xargs: /home/carl/Desktop/folder: Permission denied

```

---

### Post by Mornedhel on 2009-06-04
You forgot the cp '{}' part.

Also, please make sure the target directory exists.

kpkeerthi's script looks safer as it does some checks, while mine is really intended to be a single-use line to be used under controlled conditions.

---

### Post by LewRockwell on 2009-06-04
[transmission]

if everything in life were automated...

would there be a reason to keep the automators?

[/transmission]

---

### Post by kpkeerthi on 2009-06-04
> **kamitsukai said:**
> This gives me the same error: acouple of hundred times...=[

```
carl@carl-desktop ~ $
Copying./.plcp: line 35: [: too many arguments

```

LOL... I gave you that pseudo-code so you will have something to start off. Thats why I mentioned it as "nearly complete". Here is a cleaned up & tested one. Currently, the script ignores the lines that are commented out in .m3u files. You may have to tweak it a bit depending upon how unclean your playlist files are.

```

#!/bin/bash

print_usage() {
        echo "Usage: $0 -p playlist-file -t target-folder"
        echo
        echo "Example: "
        echo "$0 -p myplaylist.m3u -t ./Music/Playlist/Files"
        echo
}

playlist=
target=

while getopts ":p:t:" opt; do
        case $opt in
                p )
                        playlist=$OPTARG
                        ;;
                t )
                        target=$OPTARG
                        ;;
                \? )
                        print_usage
                        exit 1
                        ;;
        esac
done

if [ -z "$playlist" ] || [ -z "$target" ]; then
        print_usage
        exit 1
fi

{
	let count=0
        echo "Copying files:"
        while read file; do
		comment="${file:0:1}"
		if [ -n "$file" ] && [ ! "$comment" = "#" ]; then
		        if [ -f "$file" ]; then
				if [ \( $count -gt 0 \) -a \( $((count%40)) -eq 0 \) ]; then
					echo
				fi

		                echo -n "."
		                cp "$file" "$target"
				let count+=1 
		        fi
		fi
        done

	echo
        echo "$count files copied to $target"

} < "$playlist"

exit 0

```

**Script output (with progress indicator):**
```

keerthi@DELL-XPS-G2:~/Music$ ./plcp -p ~/Music/Ilaiyaraja\ Selected.m3u -t ~/Temp
Copying files:
........................................
........................................
........................................
........................................
........................................
................
216 files copied to /home/keerthi/Temp

```

---

### Post by kamitsukai on 2009-06-04
That's Brilliant! exactly what I wanted! Makes it much easier now to put music on my mp3 player without having to hunt through for my favourites =]

although to get mine to work I had to do:
> ./plcp -p ~/Music/Owned\**/Popular.m3u** -t ~/Desktop/Popular

Otherwise there wouldn't be a forward slash and there'd be a space in the path to the playlist =]

Thanks again!

PS: Ever thought of making this into a plugin for Rhymbox? I don't how much more effort that would take? it would be great to just right click on a playlist and select "copy audio files to portable device"

---

### Post by kpkeerthi on 2009-06-05
> **kamitsukai said:**
> 
Otherwise there wouldn't be a forward slash and there'd be a space in the path to the playlist

The standard bash rules concerning spaces and slashes in file names and paths apply as this is nothing but a bash script.

> **kamitsukai said:**
> 
PS: Ever thought of making this into a plugin for Rhymbox? I don't how much more effort that would take? it would be great to just right click on a playlist and select "copy audio files to portable device"
Nice idea. Will investigate. I have no clue how to extend rhythmbox with plugins at the moment.

**Tip:**
You may want to move plcp to /usr/local/bin (that's where I keep all my custom shell scripts). You should, then, be able to run it without the referring to its full path, just like any other standard linux command:
```

**plcp** -p ~/music/myplaylist.m3u -t ~/media/Player

```

---

### Post by kamitsukai on 2009-06-05
> **kpkeerthi said:**
> The standard bash rules concerning spaces and slashes in file names and paths apply as this is nothing but a bash script.


Nice idea. Will investigate. I have no clue how to extend rhythmbox with plugins at the moment.

**Tip:**
You may want to move plcp to /usr/local/bin (that's where I keep all my custom shell scripts). You should, then, be able to run it without the referring to its full path, just like any other standard linux command:
```

**plcp** -p ~/music/myplaylist.m3u -t ~/media/Player

```

Great thanks very much:D

I'm going to have to make sure I keep a backup of all these scripts that I've accumulated now;)

---

