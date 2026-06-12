---
title: "Recommendations for a command line (terminal) only address book for storing contacts"
date: 2010-04-01
forum: New to Ubuntu
---

### Post by pararoly on 2010-04-01
Hi Folks

Can anyone recommend a command line only address book. I want something fairly simple and efficient for storing basic contact information. All standard stuff like: Name, postal address, phone numbers, emails, urls, notes etc. The total number of contacts will be < 500 and is just for a single user (me).

I have installed "abook" which seems to be quite reasonable. Just wondered if there were any other options....

In addition, abook apparently integrates with mutt - which for me, is good.

Many thanks
Best wishes
Roly

PS, I *guess* there is an emacs address book - but I am not sure that I am ready to take on emacs just now! haha!

---

### Post by Chesamo on 2010-04-01
I don't believe such a thing exists. Your next best thing is a tab-delimited file edited in emacs.

I've been using gfa (sudo apt-get install gfa), though I can't vouch for its ability to integrate with mutt.

---

### Post by pararoly on 2010-04-01
Hello Chesamo

Thank you for your reply. :-). 

> Your next best thing is a tab-delimited file edited in emacs.

A knowledgeable friend of mine responded with the following:-

"This is the sort of classic thing that *nix was very good at way back.. and it still is, but it did require a lot of experience/learning.."

...he went on to suggest...

"the basic colon-separated file:

name: addressLineOne: adressLineTwo: City: State: Postcode: HomeTel ... etc etc

lines and lines like this can be indexed, sorted, searched, printed and so on with a few simple command-line tools - grep, sort, cut, mayby even awk... and a few shell-scripts to put them together - and, if you need to, it's still plain-text and human readable (and editbale with vim) for when the tools you use fail..."

I guess this is a similar solution to your tab separated file. 

Is gfa a command line program?

Many thanks
Best wishes
Roly :-)

---

### Post by mobilediesel on 2010-04-01
> **pararoly said:**
> Is gfa a command line program?

Looks like gfa is a GTK+ program. I'm also looking for a decent address book type program for the command line. The closest I found so far is [todo.txt]("http://wiki.github.com/ginatrapani/todo.txt-cli/"). It's primarily a todo-list manager but you can tag entries based on project names or context. It can probably be used as a simple address book as it just stores info in a text file.

---

### Post by pararoly on 2010-04-01
Hi [mobilediesel]("http://ubuntuforums.org/member.php?u=575202")

> Looks like gfa is a GTK+ program

Ok. thanks. :-)

> I'm also looking for a decent address book type program for the command line.

Did you have a look at abook.

```
sudo apt-get abook
```It is actually quite close to what I was looking for - However, I did suspect, that linux would have quite a few options in terms of command line address books. Especially, when you consider its large command line heritage.

I might just have a go at using a text file and using some of the great programs like grep, cut, sort etc - as my more experienced friend suggested. 

> It's primarily a todo-list manager but you can tag entries based on project names or context.

cool - ok. Changing the subject slightly - I do use a command line todo list. I find it really good. I did have to create a directory structure in which to "house" my todo lists however. It is called devtodo [http://sourceforge.net/projects/devtodo/](http://sourceforge.net/projects/devtodo/)

Best wishes
and thank you! :-)
Roly

---

### Post by undecim on 2010-04-01
I say go with colon delimited list, learn some basic awk, and make bash scripts to parse it.

Hmm... this sounds like a fun project. I need to learn awk.

What kind of features would this address book need? I'm in a bash-scripting kind of mood right now.

---

### Post by mobilediesel on 2010-04-01
> **pararoly said:**
> Did you have a look at abook.

```
sudo apt-get abook
```It is actually quite close to what I was looking for - However, I did suspect, that linux would have quite a few options in terms of command line address books. Especially, when you consider its large command line heritage.

I might just have a go at using a text file and using some of the great programs like grep, cut, sort etc - as my more experienced friend suggested. 

cool - ok. Changing the subject slightly - I do use a command line todo list. I find it really good. I did have to create a directory structure in which to "house" my todo lists however. It is called devtodo [http://sourceforge.net/projects/devtodo/](http://sourceforge.net/projects/devtodo/)

Best wishes
and thank you! :-)
Roly

Abook looks simple enough. I like how it keeps data in a simple text file. Text files are pretty future-proof especially considering they predate the personal computer.
Devtodo may be worth a try, as well.

> **undecim said:**
> I say go with colon delimited list, learn some basic awk, and make bash scripts to parse it.

Hmm... this sounds like a fun project. I need to learn awk.

What kind of features would this address book need? I'm in a bash-scripting kind of mood right now.

I just found [this short article]("http://www.linux.com/archive/feed/57894") showing a few commands to use in setting up your own contact management. No complete script or anything but it wouldn't be hard to set it up in a script or as aliases.

---

### Post by pararoly on 2010-04-01
> **undecim said:**
> I say go with colon delimited list, learn some basic awk, and make bash scripts to parse it.

Hmm... this sounds like a fun project. I need to learn awk.

What kind of features would this address book need? I'm in a bash-scripting kind of mood right now.

Hi Undecim :-)

Two people have now suggested going with the colon delimited list; awk and bash scripts. Since I want to learn about awk et al I think this is the way I will go. 

In terms of features - not many. 

Perhaps a script that locates and "nicely" presents a record/contact. I guess the script would grep to get a set of contacts which matched. The user then selects which contact they want displayed (or are all matched records displayed?)

Basically something which takes the colon separated data...

roland ramsbottom: the cottage : The lane : the town : postcode : 01803 555 999 : [EMAIL="roland@email.com"]roland@email.com[/EMAIL]

and re-presents it, "nicely" on the standard out....

Roland Ramsbottom
   Tel 01803 555 999
   [EMAIL="roland@email.com"]roland@email.com[/EMAIL]
   The Cottage,
   The Lane,
   The Town,
   Postcode.

I guess the above is simply the (bash script) parsing, that you already suggested would be needed?

Perhaps a script to remove a record, although cut (or other command) could be used. Personally, I think if it can be done with existing command line tools, then it should. The only reason I wanted a search and display facility was so I did not have to look at single lines of colon de-limited data. haha!

If you do put something together, please would you mind throwing some comments in there - It's been a long time since I have done any programming and I have not really written a bash script or used awk before! - But this is the point of dong this; so I learn! 

What do you think?

Many thanks - Best wishes
Roland

---

### Post by pararoly on 2010-04-01
> **mobilediesel said:**
> Abook looks simple enough. I like how it keeps data in a simple text file. Text files are pretty future-proof especially considering they predate the personal computer.
Devtodo may be worth a try, as well.

I just found [this short article]("http://www.linux.com/archive/feed/57894") showing a few commands to use in setting up your own contact management. No complete script or anything but it wouldn't be hard to set it up in a script or as aliases.

Hi Mobildiesel :-)

I am pleased you like abook - I thought it was a good little program and I also liked the fact the data is kept in a simple text file. The only "bad" point, I thought, was that the text file is in a sort-of windows format, using a [header]. I think it would be easier to manipulate contacts if the data was on a single, de-limited line. This is because most of the command line tools (grep, cut etc) seem to work with a single line by "default". If that makes any sense? What do you think?

I am going to start using abook in the interim, whilst I dream up further plans! haha!

That article, by the way, was spot on. Exactly the sort of thing I'm aiming at. Although, ours can be far more simple - at least for my own purposes it can :-). It might be worth undecim having a quick look at the article....???

Best wishes
Roly :-)

---

### Post by mobilediesel on 2010-04-03
> **pararoly said:**
> Hi Mobildiesel :-)

I am pleased you like abook - I thought it was a good little program and I also liked the fact the data is kept in a simple text file. The only "bad" point, I thought, was that the text file is in a sort-of windows format, using a [header]. I think it would be easier to manipulate contacts if the data was on a single, de-limited line. This is because most of the command line tools (grep, cut etc) seem to work with a single line by "default". If that makes any sense? What do you think?

I am going to start using abook in the interim, whilst I dream up further plans! haha!

That article, by the way, was spot on. Exactly the sort of thing I'm aiming at. Although, ours can be far more simple - at least for my own purposes it can :-). It might be worth undecim having a quick look at the article....???

Best wishes
Roly :-)

I have a fairly rough version of a contact manager. You can download it [here]("http://dl.dropbox.com/u/1055489/scripts/contacts").
Just put it somewhere in your path (I use $HOME/bin) and make sure it's set as executable.
```
chmod +x contacts
```
It creates a default config file and shows you the location and contents. It should be self-explanatory what you might need to edit.

I'm not an expert in awk by a long shot so if anyone has any improvements, please share!

---

### Post by pararoly on 2010-04-03
Hi Mobilediesel,

That's **brilliant**! well done! I have downloaded it and will have a play about later on today. Update shortly.

Best wishes
Roly :-D

---

### Post by mobilediesel on 2010-04-04
> **pararoly said:**
> Hi Mobilediesel,

That's **brilliant**! well done! I have downloaded it and will have a play about later on today. Update shortly.

Best wishes
Roly :-D

I'm still figuring out the best way to edit records with the script. It's easy enough to load the datafile into an editor and do that but I'd like the script to handle it as well. I'm still playing with a couple ideas on it that won't add too much complexity.

---

