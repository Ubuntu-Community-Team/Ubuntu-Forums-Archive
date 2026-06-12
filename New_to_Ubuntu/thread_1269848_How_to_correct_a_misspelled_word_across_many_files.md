---
title: "How to correct a misspelled word across many files simultaneously?"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by swarup on 2009-09-18
I have hundreds of text files with which I work, and in different languages. When I come across a word which has been spelled wrong in say, 80 different files, is there a tool or program which will execute the spelling change in all 80 files simultaneously? This will save me a huge amount of time, not having to open all 80 files to make the change.

---

### Post by scragar on 2009-09-18
```
cd /path/to/folder/with/files/in
for i in *; do
  echo "editing $i"
  cp "$i" /tmp/clone
  sed 's/**FROM**/**TO**/' /tmp/clone > "$i"
done
```

---

### Post by swarup on 2009-09-18
1. I see, great. So, here wherever you have put "i", I just paste the wrongly spelled word, and, the correctly spelled word I should paste where you have used the word "clone". Correct?

The only other thing I need to change in the code you've given, is to cd to the folder I need to make the changes in. Everything else will remain exactly as you've given it here. That is, the "*", "$", "temp", and "sed" will remain just as they are. Correct?

2. You sound quite knowledgeable. Would it be possible to make a simple script for this, so I don't have to rewrite the code every time? Something wherein the folder location and everything else would be preset, and I could just supply the incorrect and correct word?

---

### Post by Bölvaður on 2009-09-18
yes this will work for any textfiles. So if your files are .odt, .doc or something even worse (if there exists anything worse) then it will most likely not work, unless if your middle name is *lucky*.

---

### Post by Gwasanaethau on 2009-09-18
> **swarup said:**
> 1. I see, great. So, here wherever you have put "i", I just paste the wrongly spelled word, and, the correctly spelled word I should paste where you have used the word "clone". Correct?

The only other thing I need to change in the code you've given, is to cd to the folder I need to make the changes in. Everything else will remain exactly as you've given it here. That is, the "*", "$", "temp", and "sed" will remain just as they are. Correct?

2. You sound quite knowledgeable. Would it be possible to make a simple script for this, so I don't have to rewrite the code every time? Something wherein the folder location and everything else would be preset, and I could just supply the incorrect and correct word?

I have to admit, scragar's post was perfect, but not very descriptive.

The only bits you need to change are [b]/path/to/folder/with/files/in
[/b] to wherever it is the mis-spelled files are, **FROM** needs to be changed to the mis-spelled word itself, and **TO** needs to be changed to the correct spelling.

Best to make a back up in case it changes other words in those files that you don't want to be changed.

You can put this in a script by doing as follows:
```
#!/bin/bash
cd /path/to/folder/with/files/in
for i in *; do
  echo "editing $i"
  cp "$i" /tmp/clone
  sed "s/${1}/${2}/g" /tmp/clone > "$i"
done
```

In that case, all you need to change is the line beginning with **cd** to wherever it is you have your files. To run it, you need to make your script executable:
```
chmod u+x **script.sh**
```
replacing **script.sh** with whatever it is you called your script. You can then run it with:
```
./script.sh "**incorrect-word**" "**correct-spelling**"
```

---

### Post by swarup on 2009-09-18
> **Gwasanaethau said:**
> I have to admit, scragar's post was perfect, but not very descriptive.
ok, I see now. What you have written is very clear.
Just a couple follow-up questions.
> **Gwasanaethau said:**
> Best to make a back up in case it changes other words in those files that you don't want to be changed.
ok, I'll certainly keep a back-up in case. But assuming the code is correctly written, and you feel it is, then it would not change any words other than the designated one right? After all, it isn't going to be an easy job for me to go through all those files looking for *other* words that might have been wrongly changed. If it is going to be like that, then I'll save time by just opening each file myself and doing search and replace for the word I need. That at least is quite safe. I just want to be clear in my own mind about the predictability and security of this code. Because it is something I will use a lot, and these are very important files.

And by the way, they are just .txt files made in gedit.


> **Gwasanaethau said:**
> You can put this in a script by doing as follows:
```
#!/bin/bash
cd /path/to/folder/with/files/in
for i in *; do
  echo "editing $i"
  cp "$i" /tmp/clone
  sed "s/${1}/${2}/g" /tmp/clone > "$i"
done
```

In that case, all you need to change is the line beginning with **cd** to wherever it is you have your files. To run it, you need to make your script executable:
```
chmod u+x **script.sh**
```
replacing **script.sh** with whatever it is you called your script. You can then run it with:
```
./script.sh "**incorrect-word**" "**correct-spelling**"
```
Great. One follow-up question: how will the script know that "incorrect word" is meant to replace what you designated as {1} in the script, and "correct-spelling" is meant to replace what you designated as {2}? Where is the assignment that links these values?

---

### Post by CatKiller on 2009-09-19
> **swarup said:**
> Great. One follow-up question: how will the script know that "incorrect word" is meant to replace what you designated as {1} in the script, and "correct-spelling" is meant to replace what you designated as {2}? Where is the assignment that links these values?

${1} is a way to refer to the first argument, ${2} is a way to refer to the second, and so on. This is implicit in the shell. There is a name for this behaviour, but I can't remember what it is at the moment.

The fact that the first argument is the incorrect word and the second is the correct word (rather than the other way round) is simply because that's how it's used in the script. You might want to check **man sed** to see what's actually being done by this script.

---

### Post by Gwasanaethau on 2009-09-19
> **swarup said:**
> ok, I see now. What you have written is very clear.
Just a couple follow-up questions.

ok, I'll certainly keep a back-up in case. But assuming the code is correctly written, and you feel it is, then it would not change any words other than the designated one right? After all, it isn't going to be an easy job for me to go through all those files looking for *other* words that might have been wrongly changed. If it is going to be like that, then I'll save time by just opening each file myself and doing search and replace for the word I need. That at least is quite safe. I just want to be clear in my own mind about the predictability and security of this code. Because it is something I will use a lot, and these are very important files.

And by the way, they are just .txt files made in gedit.



Great. One follow-up question: how will the script know that "incorrect word" is meant to replace what you designated as {1} in the script, and "correct-spelling" is meant to replace what you designated as {2}? Where is the assignment that links these values?

A very good point you made about not having to go through the files again! My apologies for not seeing that in advance. 8-[#-o If you want to ensure that it's only whole words that are replaced, you can put spaces around **${1}** and **${2}**. That is, change the line:
```
sed "s/${1}/${2}/g" /tmp/clone > "$i"
```
to:
```
sed "s/ ${1} / ${2} /g" /tmp/clone > "$i"
```

The downside to that is it won't match at the ends of sentences or anywhere else that there might be punctuation. I'll try and come up with something that'll solve that problem.

P.S. Sorry I'm so long getting back to you too!

---

### Post by Gwasanaethau on 2009-09-19
OK, I've found a solution (I think):
```
#!/bin/bash
cd /path/to/folder/with/files/in
for i in *; do
  echo "editing $i"
  cp "$i" /tmp/clone
  sed "s/\<${1}\>/${2}/g" /tmp/clone > "$i"
done
```Here, the **\<** and **\>** symbols tell sed to only change the incorrect word if (and only if) it is a whole word by itself (it can be surrounded by spaces and/or punctuation). For example, say you had a file called 'colour.txt' in your home directory that contained the following:
```
color
color-catcher
bronze-color
"color!" I said.
Any more color?
They used the color.
I used it, (color, that is).
that's a color/tint.
colored
```and you ran the script with this command (to change from the North American to English spelling):
```
script.sh "color" "colour"
```you would get:
```
colour
colour-catcher
bronze-colour
"colour!" I said.
Any more colour?
They used the colour.
I used it, (colour, that is).
that's a colour/tint.
colored
```Notice how all instances of [COLOR=Green]**color**[/COLOR] have now become [COLOR=RoyalBlue]**colour**[/COLOR], but the word **[COLOR=Green]color[/COLOR]ed** has remained unchanged.

I hope this is what you're looking for. Best of luck with it. If you have any more questions, don't hesitate to ask! :cool:

[SIZE="1"]Some interesting references:
[1][http://www.grymoire.com/Unix/Regular.html]("http://www.grymoire.com/Unix/Regular.html")
[2][http://www.grymoire.com/Unix/Sed.html]("http://www.grymoire.com/Unix/Sed.html")[/SIZE]

---

### Post by swarup on 2009-09-20
Gwasanaethau: thank you heartily for all the research you've done and the information and code you've provided. It looks like you've come up with a formula which should work really well. I'll try it out, and will report back here when I do.

CatKiller: That is very meaningful and helpful information, thank you. :)

---

### Post by falconindy on 2009-09-20
Just to note, it's unnecessary to make a copy of a file with sed if you're not going to use it as a backup. The -i flag lets you edit files in place.

---

### Post by Gwasanaethau on 2009-09-25
> **swarup said:**
> Gwasanaethau: thank you heartily for all the research you've done and the information and code you've provided. It looks like you've come up with a formula which should work really well. I'll try it out, and will report back here when I do…You're very welcome! I'm just glad I was able to help!

---

