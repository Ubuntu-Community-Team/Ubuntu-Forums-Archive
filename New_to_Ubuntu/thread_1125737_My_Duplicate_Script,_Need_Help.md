---
title: "My Duplicate Script, Need Help"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by altech6983 on 2009-04-14
Hello,

Okay so what I am doing is writing a Music Duplicate Remover because I haven't found one on the web. The objective is to remove the file that is a duplicate and has the lower bitrate based on matching Title and Artist tags (probably do something with length to).

I am doing it in bash and learning as I go (yes I know it would probably be more efficient to do it in perl or something like that). I have already figured out how to read the id3 tags and parse them for the title and artist and I have a good plan for the rest of the code.

My problem stems from spaces in the file names (I bet that is the number one problem with noobs and scripts)

```
#!/bin/bash
p=0
n=2

ls >> temp.list
old_IFS=$IFS
IFS=$'\n'
patharray=($(cat temp.list))
IFS=$old_IFS
rm temp.list

#echo "1"
#echo ${patharray[$p]}
infoarray[2]="a"
while [[ ${infoarray[$n]} != "" ]]
	do
	(( n++ ))
	path=${patharray[$p]}
echo $path
	export temp=`id3v2 -l ${path} | grep "^Title" | awk '{print $'$n'}'`
	infoarray[$n]=$temp
echo ${infoarray[$n]}
done
#echo "2"
(( n-- ))
n=3
while [[ ${infoarray[$n]} != "Artist:" ]]
	#echo ${infoarray[3]}	
	#echo ${infoarray[$n]}
#sleep 2
	do
	title[$p]="${title[$p]} ${infoarray[$n]}"
	(( n++ ))
	#echo ${title[$p]}
done
(( n++ ))
while [[ ${infoarray[$n]} != "" ]]
	do
	artist[$p]="${artist[$p]} ${infoarray[$n]}"
	(( n++ ))
done
#echo "4"
```

Okay at the begining I read a list of the files in to a temp file and then bring that file in to an array "patharray" line by line. Then I assign path=patharray[$p] where p is a global counter that synchronises the file name,title, and artist array writing. Then the line
 
```
export temp=`id3v2 -l ${path} | grep "^Title" | awk '{print $'$n'}'`
```

puts the first word into the variable temp. From there I build the Title and Artist into and array by a recursive method (while loops). The problem I am having now is that when I wrote the code it was for a single file for testing purposes. The above line originally looked like

```
export temp=`id3v2 -l "Zero 7 - 03 - In the Waiting Line.mp3" | grep "^Title" | awk '{print $'$n'}'`
```

This originally worked but when I changed to the ${path} variable it wouldn't read the line as a whole because of the spaces and I have tried everything I can think of, quotes, inside and out, and before, and assigning to a non array variable (the reason you see me assigning patharray[$p] to path) but it still doesn't work

I know I have to to be missing something very simple but I have only written one other script and that one wasn't very hard.

Also if you know a better way to do this please tell me.

Thanks for any help,
Alb

---

### Post by aktiwers on 2009-04-15
Fdupes works good for me. Cleaned out a couple of GB mp3's that was all dupes.
[http://netdial.caribe.net/~adrian2/fdupes.html]("http://netdial.caribe.net/%7Eadrian2/fdupes.html")

[http://linux.die.net/man/1/fdupes](http://linux.die.net/man/1/fdupes)  <-- man page

I believe its in repos.

---

### Post by KyleBrandt on 2009-04-15
Bash uses what is called word splitting.  So it uses whatever the IFS variables is set to determine what to split up into tokens.  You need to path in double quotes: "${path}"

Observe:
```

$ foo='arf arf'
$ touch $foo
$ ls -l
-rw-rw-r-- .... arf
$ touch "$foo"
$ ls -l
-rw-rw-r-- ... arf
-rw-rw-r-- ... arf arf

```

---

### Post by altech6983 on 2009-04-15
Ha, that is just too funny. Tell you in a second.

I did look at fdupes but the problem is most of my duplicates are a plus or minus one or two second lenght, so a search that uses exact size won't work.

Now, KyleBrandt: I was going to just answer back without trying it because I had already tried it but I figured it couldn't hurt, so I did it and sure enough infoarray still came back empty, I was just about to come post when I noticed something, the file it was trying to work on was a m4p not a mp3 :mad: :cry: . I have always considered my collection to be mp3 because I only have about 20 m4p so I didn't even think about it breaking my script and of course out of all the files (4250) the first one the script works on is a m4p :o :stare: .

Thanks for the help and the suggestions the whole thing works now so I just have to finish coding the other parts, dup finding and comparing and the such.

---

### Post by PGScooter on 2009-05-29
altech,

I think this is a great idea!

I believe there is a lot of demand for a duplicate-remover program specific to music files. See two recent threads looking for such a tool here:

[http://ubuntuforums.org/showthread.php?t=1086047](http://ubuntuforums.org/showthread.php?t=1086047)
[http://ubuntuforums.org/showthread.php?t=1166739](http://ubuntuforums.org/showthread.php?t=1166739)

I will post there and refer them to this thread. I am interested also so I will keep tabs on your progress. If you want any help, let me know. I am pretty comfortable in Perl but do not have experience in bash.

---

### Post by altech6983 on 2009-05-30
Thanks for the support, I haven't been able to work on it any further, lots of things have happened from then to now, jury duty, two big rains that took out two fences (I live on a ranch), etc. I should be able to get back to work on it in the next few days.

If you can think of any better way to compare the name and such than just sorting them in an array and running through the array and comparing them (seems like that isn't very efficient but I can't think of a better way), even if it is in Perl it may give me an idea how to do it in bash.

Thanks and I will see what I can do.

---

### Post by PGScooter on 2009-05-31
hey altech,

I didn't mean to put pressure on you :)  I just thought it would be fun to try to organize some support.

As for the name comparison, do you want to only consider something a duplicate if it has the exact same name? I think you are right to worry about speed. I think I could actually write this part of the script if you want. Here is what I would do: in the part of the code where you add the file to the array, at the same time declare a variable, called $existsSONGNAME where SONGNAME is the name of the song. Then, when you want to see if a songname exists, just check to see if the variable $existsSONGNAME is declared or not. Does that make sense? Did I understand your question correctly? By the way, I am just a beginner so I do not know if that is a good way or not. We could always post on the programming subforum to get some help.

---

### Post by altech6983 on 2009-06-01
When I said name I mean't all of the other properties also (I figured if I found a good way to compare the name then it would work for everything else). Right now I am looking at comparing name, artist, lenght (+/- maybe 5 or ten seconds), in that order, then find which one has the higher bitrate and delete the other.

Don't worry about the pressure, I really didn't take it that way, I hadn't really had much time to work on it and it wasn't all that high of a priority because it didn't seem that anyone else wanted it so I figured I would finish it when I finish it, but now that even just one person wants it I want to get it finished, you know, so as to not just let it sit around and let the idea die.

I like the way you said to do it, it seems pretty efficent for getting that first match, after that then it shouldn't be to hard for the rest. The only problem is I don't know if you can "auto" declared a variable like that in bash (sounds like a higher programming language function to me), all I have ever done is a=1, ghook="string", etc. Right now I am in the process of overclocking my PC somemore (just started doing Folding@HOME and I want a better PPD), I was at 3.5 Ghz (3.0 Ghz stock) and I am going for 3.8 to 4.0 Ghz, so right now I am prime95 testing it (CPU stability) in windows so I don't have access to bash. I should be done in about a day or so and I will try that then.

PS This script will only work with mp3 files (uses the program id3v2 to get tags) but after I have the mp3 part working I want to expand it to work with mp4 and others.

---

### Post by PGScooter on 2009-06-02
Sounds like an excellent plan, although a bit ambitious/impressive for what I would be able to do.

There is actually a function "declare" that is part of bash, which has several options associated with it.

good luck on the overclocking

---

### Post by altech6983 on 2009-06-02
I was looking at python for a bit while I was stability testing and it looks like it is a much better language to learn than bash. I started looking at porting over the code and it doesn't seem like it would be to hard plus I read about this really cool Dictionary function that I think can do just what I need.

This is how I think it would work (This is just a higher order map).

Get list of path to mp3 files in a directory (i.e. ./hello - byme.mp3 ...)
Write that to a list, pathlist
Find someway to parse the id3v2 tags for the name, artist, length (is that even stored in the id3v2 tags), and bitrate (again in the id3v2 ?)
Write the name to a dictionary in the formate of name['song']=n where n is a index variable that runs from 0 to number of files, also before each write it runs a 'song' in name, if false then appends it to the dictionary, if true it retreives the index number stored with it and goes from there.

How about that, do you think that will work?

PS. When I start a project, I start them big (even if I don't know what I'm doing :-) ), whether it hits the wallet or the brains.

----------------------------------------------------------------------------------------

Here is what I have so far. (I suggest you copy it into your favorite editor, I just use gedit but the color coding helps so much)

```
#Still need to add the code to deal with blank spot in the title, artist, lenght, or bitrate.
import os
from mutagen.id3 import ID3

print "Please input the directory you would like to scan for mp3 duplicates:"
path = raw_input()
os.chdir(path)

rawfilename = os.listdir('./') #Creates a variable containing all files in current directory

i = 0
filename = [] #Creates a empty list

#This block of code filters out all files except mp3's and does preliminary duplicate testing by comparing filenames
for i in range(0,len(rawfilename)):
	if rawfilename[i].endswith(".mp3"): #Makes sure that what it takes in is a mp3 file
		if filename.count(rawfilename[i]) == 0: #Checks to see if the current file name is in filename list already
			filename.append(rawfilename[i]) #It was not in the list so append it
		else: #It was in the list so compare and delete the worst file.
			titlematch = if title(filename[filename.index(rawfilename[i])]) == title(rawfilename[i]): 1 #Check to see if there is a title match, if so titlematch = 1, if not 0
			artistmatch = if artist(filename[filename.index(rawfilename[i])]) == artist(rawfilename[i]): 1 #Check to see if there is a artist match, if so artistmatch = 1, if not 0
			lenghtmatch = if (round(lenght(filename[filename.index(rawfilename[i])]))-5) <= round(lenght(rawfilename[i])) and (round(lenght(filename[filename.index(rawfilename[i])]))+5) >= (round(lenght(rawfilename[i])): 1 #Check to see if there is a lenght match, if so lengthmatch = 1, if not 0
			file1 = if bitrate(filename[filename.index(rawfilename[i])]) > bitrate(rawfilename[i]): 1
			file2 = if bitrate(filename[filename.index(rawfilename[i])]) < bitrate(rawfilename[i]): 1
			if math.fabs(bitrate(rawfilename[i])-bitrate(filename[filename.index(rawfilename[i])])) < 1000:
				if round(lenght(filename[filename.index(rawfilename[i])])) > round(lenght(rawfilename[i])):
					pass #If filename time is greater then delete rawfilename[i] and remove from rawfilename list
				elif round(lenght(filename[filename.index(rawfilename[i])])) <= round(lenght(rawfilename[i])):
					pass #If rawfilename time is greater then delete filename[filename.index(rawfilename[i])], remove from filename list, and append rawfilename
			else:
				if file1 = 1:
					pass #If file1 has the higher bitrate then delete file2, rawfilename[i] and remove it from the rawfilename list
				elif file2 = 1:
					pass #If file2 has the higher bitrate then delete file1, filename[filename.index(rawfilename[i])], remove it from the filename list and append rawfilename[i] to filename list
def title(filename):
	
def artist(filename):
	
def lenght(filename):
	
def bitrate(filename):
	
```

---

### Post by PGScooter on 2009-06-05
altech,

seems like a great start and a good plan. As for yanking out all of the data, I think you will need to use modules, or perhaps bash commands (even though you are using python, you can still call bash commands, but I think it's best to do as much in python as you can). I wish I knew python :)

---

### Post by altech6983 on 2009-06-05
Aw crap, when I read your post I got it stuck in my head that you knew python and so I decided to switch from bash to python so that you would be able to read the code better and be able to help easier. Dang those two P programming languages. Oh well :-(

I already have a module that reads and writes ID3v2 tags on many different file types so once I get done with this it will work with many types of files(so long as they use ID3v2).

---

### Post by PGScooter on 2009-06-07
haha oh well. It seems readable enough, I'm sure I could follow it. I just don't think I could e able to help, unless you wanted to have me write something in bash or perl and you just run the script in your python script. I know that's easy to do, but I do not think it is usually best to avoid mixing languages like that.

---

### Post by altech6983 on 2009-06-08
No thats fine, I would rather keep it all one language anyways. Thanks for the offer.

I ran into a small hickup but I am about to figure that out.

---

### Post by tendo on 2009-09-09
Has there been any progress on this?  I would love to have this functionality on my server!  Unfortunately I'm not much of a programmer.

:guitar:

---

### Post by PGScooter on 2009-09-09
I'm not sure if altech is still working on it.

---

### Post by altech6983 on 2009-09-10
Sorry Guys, I guess I should have posted an update, I had been trying to find a job all summer and I found one just a little after I last posted and have since been busy with that and now I have gone back to college. 

This is still at the top of my project list and when I get time I will work on it, I haven't been able to work on this or any other projects either.

Right now all that is pretty much left is to code the part where it parses the mp3 info, but later I plan on adding support for other formats.

I should have some free time coming up pretty soon though so maybe I can get it working then.

---

### Post by PGScooter on 2009-09-11
altech,

thanks for the update. I have definitely been there before!

I just finished a script that converts a music folder (and subfolders) into ogg. It's nothing impressive, but it's a mirror script.. so whenever you add an mp3 to the collection, this script will find that new one and convert just it to your mirror. I can't imagine anyone else wanting to convert lossy mp3s (and m4as and wmas) to lossy oggs but I thought I would post.

good to know your script is still on the backburner!

---

### Post by altech6983 on 2009-09-25
Okay, this link is a new thread that contains the alpha v0.00000001 ;-)

[http://ubuntuforums.org/showthread.php?t=1275469](http://ubuntuforums.org/showthread.php?t=1275469)

Test it out and let me know if you have any problems.

P.S. If you could, would you post the part of your script that does the mirroring detection?

---

