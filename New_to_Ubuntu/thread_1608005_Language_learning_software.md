---
title: "Language learning software"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by alzaf on 2010-10-28
I am currently studying to learn the ) Gàidhlig (Scottish Gaelic language and finding studying by rote out of a book a bit 'limiting'. 

Because of this, I am thinking about creating a software project which could act as an interactive way to helping me learn the language. I've got a few ideas floating in my head but the direction I want to take is that the software is not an alternative  but  an aid to be used in conjunction with traditional studying materials. I was thinking possibly small interactive games or exercises that both are fun as well as to test and use the parts of language I have learned. There might also be a bit of reporting to show strengths and weaknesses. 

Firstly, the technical specifications, that offhand, I can think of that the project will need to meet:
[LIST=1]
[*]Cross-platform (while I would like it to be just Linux, I have to be realistic that people would rather use Windows)
[*]The language data is separate from main program so that the software can be used with other languages. 
[*]Not too complex so that it is quick and easy to program as I will be doing it myself.
[/LIST]

As I mentioned, this is just at an idea's stage and I was looking for some advice which I would be grateful to receive. I plan to write the project in C++ for cross platform compatibility, better structure of code (I don't fancy using C and GObject) and easy installation. What toolkit library is the best to use? I was thinking of either wxWidgets or QT but as the software project could involve game type animations is there any other libraries that are better suited?

I am also looking for some barnstorming ideas for content. Has anybody got any idea's that would be fun as well as educational? The ideas I have is maybe a simple card exercise showing pictures and a time limit to enter it's meaning in the given language to things like crosswords, hangman and other word-type puzzles. The thinking behind it is to constantly use the language you have learned until it becomes second nature. It is a lot more random than what you would get out of a book and to keep it interesting.   

I don't know if what I am wanting to achieve is too ambitious for what I am capable of but with your help and advice, I'll get a better idea.

---

### Post by KIAaze on 2010-10-29
cf my post here for a list of language learning tools/sites: [http://ubuntuforums.org/showthread.php?t=1566549](http://ubuntuforums.org/showthread.php?t=1566549)

This sounds like a great project.
You can find a lot of good language learning game example on [http://lernu.net](http://lernu.net) . :)

As for coding, I think C++ with wxWidgets or Qt is a good choice if you are already familiar with them.

You should be able to make simple games like hangman or memory with Qt. No need for SDL/OpenGL.
wxWidgets and GTK probably offer similar possibilities.

Python + Pygame or Python + GTK/wx/Qt might be easier if you have no C++ experience, which does not seem to be the case.

I find parsing to be a lot easier with python than with C++, but if you use available parsing libraries or formats (XML for example), this shouldn't be a big issue. Boost:regex might also help with parsing, but I don't have much experience with it yet.

P.S.: Let me know if you start the project. I might be able to contribute with coding, translations, testing, packaging, etc eventually.

P.P.S: My personal preference for GUI toolkits goes to Qt. ;)
I have no experience with wxWidgets yet. Some experience with C++/GTK, PyGTK and most with C++/Qt.

---

### Post by migs73 on 2010-10-29
This all sounds Glè Mhath!

(don't respond to me in Gaelic, I had to look that up, as I only knew the anglified Glay Va!!) :)

EDIT Its means 'very good' BTW

---

### Post by alzaf on 2010-10-29
Thanks for the kind words, much appreciated.

Up to now I have been studying pronunciation using the IPA method. migs73, the Anglicised Glè Mhath you mentioned is pretty much how it is pronounced (Gàidhlig in it's written form is a pretty sophisticated system of expressing pronunciation, very hard to get your head round it in the beginning but it is starting to make sense lol)

To the project, the motivation behind it is as I am now starting grammar I was thinking if a software solution could aid me in it. I had originally thought of a type of chat-room experience where simple conversations could be carried in that language via myself and the software (the software mimicking a real person). As I got to think about it, I realised that this going to be a complicated task as I want this to be multi-lingual and how would the software be able to parse pieces of text in languages that will have different structures (my understanding of grammar structure in Gàidhlig is the verb first just like the way Yoda of Star Wars speaks). The other possible problem is how the software would interpret input text and start the next question (I was thinking of a sort of database structure where the software's next question is dependent on the users previous reply depending if it is possible, negative or neutral). As I thought about it, the more I realised it would be too ambitious. 

I then thought I'd better start to crawl before I walk and try something simpler as I am learning myself and try to create a sort of 'language immersion' approach where you have to start thinking about what you learning rather than just studying it using the language you already know. 

KIAaze, I was thinking along the lines of using C++/QT as from what I read the code can be compiled on Linux and Windows without too much trouble. Unfortunately I had did C++ years ago so will need to get up to speed on that as well as learn QT (my recent programming experience has been with Python and PyGTK). As I get up to speed with the language, I was thinking of creating a simple CLI based program that utilities the exercises from the book (Teach yourself Gaelic) I am studying from.

Thanks for the links. I've had a quick look and they look guid.

---

### Post by KIAaze on 2010-10-29
Python and PyGTK also run on Windows as far as I know, although I never tried cross-platform development with it. So if you feel more comfortable with it, no reason to switch to C++, except maybe for speed, or for the awesomeness of Qt. ^^

And yes, your first idea of creating some kind of chatbot definitely seems very complex.
But you could integrate IRC into your program for example, so that users can talk with each other or with teachers (cf the integrated chat on every lernu.net page).

If you want the user to write complete sentences, it might be easier to just have a list of possible answers and check against those, than to syntactically parse the sentence and check that it's grammar, spelling and meaning are correct.

For a more ludic approach, I think some kind of adventure game might be great. :)
This would of course most likely restrict it to one language, with a story where it is necessary to master a certain language in order to progress (ex: tintin-like adventure in a foreign country, or mysterious da-vinci code like secrets in another language).
[The AGS Editor source code]("http://www.bigbluecup.com/yabb/index.php?topic=42063")[ is now available]("http://ags-ssh.blogspot.com/2010/10/ags-editor-source-code-available.html"), so hopefully soon a GNU/Linux native editor, and then...

---

### Post by alzaf on 2010-10-30
I was thinking of using Python but as I wanted to make it cross-platform even possibly on the android platform I thought writing it in a compiled language so that the hassle of the end user having to install the Python interpreter and libraries.  

I agree that the chatbot program is too complex. The reason why I am not committing myself totally to this until I get a clearer idea of what I want to achieve is that I have been in this situation before with software projects and have bitten off more than I can chew. I want to plan more and make achievable targets :)

The adventure game sounds a good idea and would fit in with my idea of a language immersion environment where the only language used is the one you want to learn rather than the one you already know. 

I think what I want to do is to create mini-games like the ones from the KDE Education project but have them linked so any weaknesses can be identified that could be concentrated on when playing any of the mini-games again?

Edit:

I have checked out Kwordquiz and I find it quite useful. On thinking about it, I am going to see if the KDE language project needs help rather starting a project on my own. The way I see it more can be achieved by pooling resources rather than duplicating stuff that has already been done. It will have the benefit of support from an established community.

---

### Post by KIAaze on 2010-10-30
> **alzaf said:**
> i have checked out kwordquiz and i find it quite useful. On thinking about it, i am going to see if the kde language project needs help rather starting a project on my own. The way i see it more can be achieved by pooling resources rather than duplicating stuff that has already been done. It will have the benefit of support from an established community.

+1 :)

---

### Post by alzaf on 2010-10-30
It doesn't make make sense plodding away on our own when your essentially duplicating work. Thanks for pointing me in the right direction KIAaze

---

