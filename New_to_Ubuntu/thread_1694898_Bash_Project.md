---
title: "Bash Project"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by Rhysk on 2011-02-25
I recently switched started an ubuntu server in an effort to learn more about bash, scripting, networking, ect. I have most of the kinks worked out of the initial install of the server, but I can't learn anything from it unless I have a project for myself. 

My friend suggested trying to make a script (from here on out, I enter total noob mode, so I could use the completely wrong words to describe things) that would periodically check a torrent site for new torrent of a show, movie, ect, and download the new torrent if one appears. It would then stream the movie/show/whatever to his xbox for him to watch.

Now, I'm not asking for help on how to do it (although that is not frowned upon :)), what I am asking for is how to go about teaching it too myself. I haven't the foggiest idea what to look for tutorials on, or do research on in order to accomplish this. An analogue I can think of would be telling someone with no practical experience, expertise, or knowledge, to build a go cart. They would just see a pile of metal and a motor, and wouldn't have any idea how to go about putting it together. They wouldn't even know what welding is, and thus wouldn't be able to effectively self teach themselves to put the go-cart together. That's the feeling I'm getting when trying to think how to start this. 

Any help or helpful direction-pointing is greatly appreciated.

---

### Post by lykeion on 2011-02-25
Your friend seems a bit selfish when suggesting such a project for you I think :)

The path to learning is very different from person to person. There are the practical ones who learns by trying out for themselves, and the theoretical ones that do a lot of reading and researching to grasp the concept first. If I gave you 25 links with reading material on bash scripting it might not be that helpful if you're a practical person.

If I were a total beginner I would realise that I would need to understand the basics first. I don't know if you're familiar with a [hello world program]("http://en.wikipedia.org/wiki/Hello_world"). If you manage to write a hello world in bash it may not seem much, but you've actually mastered quite a bit through that.

Next I would need to know about basic programming stuff like variables, operators, loops, functions, parameters, etc. Google (or my new fav search engine duckduckgo.com) is a great help here. A search for "bash variables" will get you right on target. Then maybe "bash loops", and so on. Read, understand, and try the examples yourself.

Learning bash scripting is also very connected to a knowledge of unix commands like cd, mv, ls, grep, sed, awk, etc. The more you know of these commands the more you can do with bash scripting.

After going through the basics you can actually start with a simple project. Simple is key here.

---

### Post by aeiah on 2011-02-25
dont consider making a script that checks for torrents, downloads them (unpacks them...) AND streams them. that's crazy :p

i have several scripts to accomplish things like that, written in python. it would be better to have several smaller scripts that accomplish each bit. for downloading and streaming, you can use existing programs without any scripting. 

the first thing you want to do is decide what you want to accomplish, and then how you'll accomplish it, in normal human terms.

torrent sites usually announce things on an RSS feed, so your scraper script should read this and match up your key words with the relevant .torrent links. if you have your key words in a list, you can use a for loop to check if they exist in your downloaded RSS feed one at a time.

if it identifies a tv show, your script should then check a log file to see if the torrent has already been downloaded. if it hasn't, it should download the .torrent to a folder, and write a note of the torrent to the log file.

that's all there is to it really. you'll bang your head against the wall plenty of times, but if you take it one step at a time you can learn how to do the different bits.

your torrent program should be able to watch a folder for new torrents, and anything else should be done in another script. depending on how busy the torrent RSS is will depend on how often you'll want to check it. once its working, schedule the script in crontab to run every X minutes.

---

### Post by Rhysk on 2011-02-27
> **aeiah said:**
> dont consider making a script that checks for torrents, downloads them (unpacks them...) AND streams them. that's crazy :p

i have several scripts to accomplish things like that, written in python. it would be better to have several smaller scripts that accomplish each bit. for downloading and streaming, you can use existing programs without any scripting. 

the first thing you want to do is decide what you want to accomplish, and then how you'll accomplish it, in normal human terms.

torrent sites usually announce things on an RSS feed, so your scraper script should read this and match up your key words with the relevant .torrent links. if you have your key words in a list, you can use a for loop to check if they exist in your downloaded RSS feed one at a time.

if it identifies a tv show, your script should then check a log file to see if the torrent has already been downloaded. if it hasn't, it should download the .torrent to a folder, and write a note of the torrent to the log file.

that's all there is to it really. you'll bang your head against the wall plenty of times, but if you take it one step at a time you can learn how to do the different bits.

your torrent program should be able to watch a folder for new torrents, and anything else should be done in another script. depending on how busy the torrent RSS is will depend on how often you'll want to check it. once its working, schedule the script in crontab to run every X minutes.
You mentioned you have scripts in Python to accomplish some of these tasks. Is this because it is easier or because you are more familiar with python.

---

