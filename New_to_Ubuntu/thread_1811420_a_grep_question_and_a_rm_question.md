---
title: "a grep question and a rm question"
date: 2011-07-24
forum: New to Ubuntu
---

### Post by s1baker on 2011-07-24
hello group,
I have a grep command question and a rm command question.

1) how do you use grep to look through the directories and sub-directories ( recursively ) to find a certain text in only *.txt and *.doc type files?
I tried this :
```
grep "xyz" -i -r Documents *.doc *.txt
```
The directory I want to search is "Documents" and I want to
look for the text "xyz" ( whether or not it has caps ) in the directory Documents and all of the sub-folders under Documents, and I only want to search files that end in ".doc" or ".txt"


2) MS DOS has the "del" command that asks you before it deletes,
if you really are sure. "rm" doesn't do this ( although I think there is a flag that you can use with rm that verifies first, which seems redundant to me) Is there another remove file/files command that asks for a verify first, or would it have to be a script file made up by using rm?


Thanks

---

### Post by master_kernel on 2011-07-24
2. rm -i FILE is what you're looking for.

---

### Post by s1baker on 2011-07-24
> rm -i FILE is what you're looking for.


yes, but I don't want to use rm. To easy to forget the option -i
I would like one simple command to use instead of rm

---

### Post by AlphaLexman on 2011-07-24
Try this...
```
find ~/Documents -name "*.txt" -o -name "*.doc" | grep "xyz"
```

---

### Post by GWBouge on 2011-07-24
I'm not sure of another utility to use, but you could set an alias on your ~/.bashrc file.  Something like:

```
alias rm='rm -i'
```

For the grep, you want to combine it with the find command, such as:

```
grep "search_string" `find ~/Documents -name "*.txt" -o -name "*.doc"`
```

---

### Post by karlson on 2011-07-24
> **s1baker said:**
> hello group,
I have a grep command question and a rm command question.

1) how do you use grep to look through the directories and sub-directories ( recursively ) to find a certain text in only *.txt and *.doc type files?
I tried this :
```
grep "xyz" -i -r Documents *.doc *.txt
```
The directory I want to search is "Documents" and I want to
look for the text "xyz" ( whether or not it has caps ) in the directory Documents and all of the sub-folders under Documents, and I only want to search files that end in ".doc" or ".txt"


2) MS DOS has the "del" command that asks you before it deletes,
if you really are sure. "rm" doesn't do this ( although I think there is a flag that you can use with rm that verifies first, which seems redundant to me) Is there another remove file/files command that asks for a verify first, or would it have to be a script file made up by using rm?


Thanks

Let me make sure I understand.

You want to delete all files in directory "Documents" that contain text "xyz" in them and have extentions .doc and .txt?

If that's the case then do the following:

```

for each in `grep -i "xyz" Documents/*.doc Documents/*.txt | awk -F: '{print $1}'`
do
rm -i $each
done

```

2.  If you want to have rm always ask your permission then add this to your .bashrc
```

alias rm='rm -i'

```

---

### Post by s1baker on 2011-07-25
@ Karlson
```
Let me make sure I understand.
You want to delete all files in directory "Documents" that contain text "xyz" in them and have extentions .doc and .txt?
```

No, I don't want to delete any files in the Documents folder ( my learning of grep and find and rm is not at that point yet , hehe )
I was just wondering if there was a command similar to DOS del.

---

### Post by sisco311 on 2011-07-25
[list=1]
[*]
```
grep -ir 'xyz' --include='*.txt' --include='*.doc' ./
```


[*]
Use an alias.
[/list]

---

### Post by s1baker on 2011-07-25
thanks guys, I will call this resolved, but I did notice something unusual.

this command:
```
grep "xyz" -ir  Documents *.doc *.txt
```
took 25 seconds to complete.

and this command:
```
grep -ir 'xyz' --include='*.txt' --include='*.doc' Documents
```
took 1/2 second to complete.

I wonder whats up with that?

---

### Post by sisco311 on 2011-07-25
The first one searches all files (recursively) in Documents and the jpg and doc files from the current working directory. The second one does what you want.

---

### Post by ddastoor on 2011-07-25
There are of course many ways to do the same thing... As you explore linux more and more u'll find ur pet way:-

1) the grep question..  2 approaches :
a) The find command has with it the exec option. so, 
```
  find ./Documents -name '*.txt' -o -name '*.doc' -exec grep -il 'your text' \; 
```

So, everything before the '-exec' will generate the list of path filles or directories and 

```
-exec <cmd> {} \;
```

means that from that list of generated files, '<cmd>' will work on EACH file in the list (indicated by the '{}' )

Also, don't forget the '\;\ at the end without any quotes.


b) If you want <cmd> to work once on the entire generated list simultaneously, then u can try a combination of find and xargs (do man xargs for more details)

```
find ./Documents -name '*.txt' -o -name '*.doc' | xargs grep -i 'your search text'
```

(please note that xargs itself ALSO has the {} option for working on each item in the list; see man xargs)

hope this helps

---

### Post by s1baker on 2011-07-25
Thanks all, that pretty much answers my questions on the grep search and using an alias to make rm always use rm -i before any deletes.
 This brings up a question about using the terminal to do deletes. 
It would seem that an alias could be made to use the mv command to remove files ( instead of rm ), so that any files that a person wanted to delete would not be deleted permanently,  but moved to a folder that a person has set up, call it "mytrashcan" or whatever, and then later, that person could go and delete their trashcan, just like is done with gnome. Would that alias/script be hard to write?..and could it be done to where the alias asks for verification as to whether or not the person wants to delete ( actually move the files to the trashcan folder ) before it actually is done?

---

### Post by sisco311 on 2011-07-25
> **s1baker said:**
> Thanks all, that pretty much answers my questions on the grep search and using an alias to make rm always use rm -i before any deletes.
 This brings up a question about using the terminal to do deletes. 
It would seem that an alias could be made to use the mv command to remove files ( instead of rm ), so that any files that a person wanted to delete would not be deleted permanently,  but moved to a folder that a person has set up, call it "mytrashcan" or whatever, and then later, that person could go and delete their trashcan, just like is done with gnome. Would that alias/script be hard to write?..and could it be done to where the alias asks for verification as to whether or not the person wants to delete ( actually move the files to the trashcan folder ) before it actually is done?

You can install trash-cli from the repos and use trash to move file(s) to trash, list-trash to list the content of the trash, restore-trash to restore file(s) from the trash and empty-trash to empty the trash.

---

