---
title: "Prepending text to the begining of a file"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by pararoly on 2010-05-08
Hi All :-) 

From the command line you can append text to a file. For example:- 
```

uptime >> uptimeStats.txt

```This will append the output of uptime to the file uptimeStats.txt

Is there an equally simple way of adding the text to the begining of the file? "prepending", if you will?.  The original contents of the file must persist. 

Many thanks
Best wishes
Roly :-)

---

### Post by peculiar penguin on 2010-05-08
Not really. You could dump the text you want to prepend into a temporary file (A), append the other file (B) to it, delete or rename B, rename A to B's original name. ;)

---

### Post by pararoly on 2010-05-08
Hi peculiar penguin

Thank you for your reply, and..

Yeah, kind of what I was expecting. :-s

Many thanks
Roly :-)

---

### Post by tgalati4 on 2010-05-08
man cat
man tac

cat firstfile.txt secondfile.txt > combinedfile.txt

---

### Post by pararoly on 2010-05-08
Hi [tgalati4]("http://ubuntuforums.org/member.php?u=241895")

Thank you very much. That has got me a lot further. :-)

All I am actually trying to do is enter a new "note" from the command line and have it added to the start of a text file - full of notes. There is no order or sorting, other than chronological, to the text file.  

I tried using ...
```
cat - file2 > combined
```i.e. the dash (-) taking input from the command line. But when I press ctrl+c to finish providing my input, the entire command quits and the combined file is not updated correctly. I hope that makes some sort of sense!?

Then I tried...
```
echo "My new note, directed at the head of an existing text file" | cat - file2 > combined
```This DID work. So that's great, thank you. Any more bright ideas to make it even easier?

Many thanks 
roly :-)

edit: obviously I still then need to rename "combined" to "file2"

---

### Post by sisco311 on 2010-05-08
> **pararoly said:**
> 

I tried using ...
```
cat - file2 > combined
```i.e. the dash (-) taking input from the command line. But when I press ctrl+c to finish providing my input, the entire command quits and the combined file is not updated correctly. I hope that makes some sort of sense!?



Yes, ^C causes the active program to receive a SIGINT signal.

You have to press ^D to indicate the EOF.

[http://en.wikipedia.org/wiki/Control-C](http://en.wikipedia.org/wiki/Control-C)

[http://en.wikipedia.org/wiki/Control-D](http://en.wikipedia.org/wiki/Control-D)

---

### Post by pararoly on 2010-05-08
Hi sisco311

Awesome - I suspected there must be a different key combination.

thank you (all) for your help :-)

Best wishes
Roly

- thread solved :-)

---

### Post by sisco311 on 2010-05-08
You are welcome!

If you want to add multiple lines, instead of piping echo to the cat command you can use something like:
```
cat - file << EOF > newfile
line1
line2
line3
EOF
```

---

### Post by pararoly on 2010-05-08
Hi sisco311

Just tried that - wow, the more I learn about linux the more i love it! it works great!

Can I ask another question....

What is the "<<" operator called. If it has a name? I know that:-

> re-directs output, and 
>> appends output, so
<< this waits until the EOF (or whatever) marker is reached?

One day, I hope to become really good at linux - but it is going to take a while to learn it all! haha!

Thank you very much once more.
Best wishes
roly :-)

---

### Post by kaibob on 2010-05-08
> **pararoly said:**
> All I am actually trying to do is enter a new "note" from the command line and have it added to the start of a text file - full of notes. 


If this is something that will be done on a regular basis, you may want to add a function to your bashrc file. I have included a simple example below that is based on your command line. With this you would simply type the name of the function (adt in my example) followed by a space followed by the text to be added to the start of the text file. The text does not have to be quoted. This assumes, of course, that the name of the combined file does not change. You could dress this up in various ways--for example to insert newlines. 

```
adt () {
echo "$*" | cat - combined.txt >> .temp.txt
mv .temp.txt combined.txt
}
```

---

### Post by tgalati4 on 2010-05-08
I call it an input pipe, but I don't know it's official name.

< single  file input pipe
<< continuous input pipe until special key is pressed

Here's a reference, but they simply call it redirection:

[http://linuxdevcenter.com/pub/a/linux/lpt/13_01.html](http://linuxdevcenter.com/pub/a/linux/lpt/13_01.html)

More cool stuff with redirection:

[http://www.tuxfiles.org/linuxhelp/iodirection.html](http://www.tuxfiles.org/linuxhelp/iodirection.html)

---

### Post by pararoly on 2010-05-10
Hello Guys :-)

Sorry for delay in replying - I have been working on an essay :-s

thank you for all your help, I have swiped the script and am having a play about with it. working well so far. many many thanks :-D

[http://tldp.org/LDP/abs/html/special-chars.html](http://tldp.org/LDP/abs/html/special-chars.html)

I also found that concerning the special characters.

Best wishes
Roly (loving linux and it's great community :-D)

---

