---
title: "New to Kubuntu and has not slept since yesterday, stayed up all night and needs help"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by twilight7 on 2008-06-30
I do not know what i am doing, i need to learn to install things, i wnat to install WICD and penguin, and firefox, i am getting very frustrated, i have tried to fallow what people say to do. i dont understand it. i get lost. i need someone with good patients and can tell me as if i am a kid how to do this, i just installed kubuntu last night and i have not slept at all today. that is how long i have been working on it and reading. i dont know waht a terminal is. i am a noob so please help me. please. it would be much appreciated.       
     
Monique

---

### Post by superprash2003 on 2008-06-30
to make things easier go to system->administration->synaptic .. there in the search tab type the name of the application you want to install and then click on the tick mark next to the app and click on apply

---

### Post by kevdog on 2008-06-30
What do you need help with??  You weren't very specific.  Firefox is installed by default?  Do you need Firefox2?

---

### Post by Ayuthia on 2008-06-30
Actually, Firefox is not installed by default in Kubuntu since Konqueror is already there.  You should be able to install Firefox through Adept.  Do you have a working Internet connection?

To install wicd, you can go into Adept->Manage Repositories.  Click on the Third Party Software and click on Add.  It will bring up a screen for you to add a new repository.  You will need to add the following (assuming that you are using Hardy):
```
deb http://apt.wicd.net hardy extras
```and then click OK and then close the Software Sources window.  From there, you will need to press the Fetch Updates button and you should be able to find wicd.

As for penguin, I am not familiar with that one.

If you are looking for the Terminal in Kubuntu, it is actually called Konsole.  It should be found under System->Konsole.  This is the command line portion of Kubuntu.  It looks like DOS from the old Windows days.

---

### Post by JoeyA on 2008-07-01
Twilight7 first step back take a deep breath. Almost any program you want is in the Adept Manager Repositories.  Don't get impatient with Linux.  If your root and modify or delete a file unknowingly you could cripple your system.    The Practical Guide to Ubuntu should be an excellent source of information for you it is sold in most bookstores, don't be frightened by its girth it has a lot of pictures and examples.  These forums are also a great resource for any user. Kubuntu is fantastic, especially when compared to Vista (aka piece-0-crap).  Don't get discouraged.

---

### Post by jimbo99 on 2008-07-01
He needs an explanation of what you are telling him to do.  He doesn't understand what synaptic is.  He doesn't understand what adept is.  He doesn't understand what's necessary to install any program be it a .tar.gz or a .deb or any other.

He is thinking like the windows world he came from.  You download a file and you double click on it.  He doesn't know he can just pick from a list of available programs from a repository of provided programs online.  He doesn't even know what a repository is.

Those are key things to understand in Linux and K/Ubuntu. For him the questions are:  What is synaptic/adept?  What is a repository?  What do you mean by "adding a 3rd party source repository"?

These basic explanations are left out and there's a certain amount of prerequisite knowledge that many ppl assume you have, which he doesn't have.

Whomever pointed him to Kubuntu was wrong to do so.  Now his first experience is tainted.  He should have been put on Ubuntu to start and as far as I can tell by his writing style, to stay, forever.

I told my sister when she was first starting with computers to read from the upper left of the screen going across and to look at all the objects on the screen.  He reminds me of her.  He isn't looking at the screen, he's not associating the objects on the screen with those real life things like pushing a button to perform some action.  He needs to take his time and read.

And, why would they not put Firefox in?  I've used KDE for quite a while and it is not adequate for most people's needs, especially beginners, as there are very few references to KDE's web browser when you go out into the world of the internet.  Leaving Firefox out was a mistake.  It couldn't have been one where they were trying to eliminate bloat.  That's crazy as KDE is huge in bloat.

I'm sorry he had to go through this but he should also understand that he didn't learn what he knows about Windows overnight and he shouldn't expect to learn everything about linux overnight.

---

