---
title: "Game will not work - any alternative available?"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by Scunnered on 2009-03-03
I decided to have a look at some games only to find a couple of problems.

Firstly I downloaded billiard-gl only to find that all that will display is the opening screen, nothing else.  No menu or anything.  Clicking on the opening screen only causes my desktop to be overlaid on the billard ball.  If I keep clicking I can totally remove the display.

Can anyone offer a solution of an alternative billiard/pool game that will work?

Second problem is when I look at AisleRiot Solitaire on the add/remove it shows up a number of items which are linked to the item. But when I go to the games menu the list is not fully displayed.  How can this be displayed?

Thanking you in anticipation

---

### Post by Roanoke on 2009-03-03
Do this in a terminal (Applications->Accessories->Terminal):
```

sudo apt-cache search billiards

```
You will be asked for your password. You will then see a list of applications that pertain to the term 'billiards'. Use this (in the terminal again) to install one:
```

sudo apt-get install <name-here>

```
and this to remove an installed program:
```

sudo apt-get purge <name-here>

```

And I'm not certain what you mean by your second problem.

---

### Post by llamabr on 2009-03-03
or 

```
apt-cache search game
```

will return alot of apps.

Note that apt-cache does not require sudo, although apt-get does.

---

### Post by Scunnered on 2009-03-04
Many thanks to you both.

I will have a look at your suggestions. 

With reference to my second problem when using add / remove AisleRiot Solitaire
shows a rather large list of games as being linked with that download but if I want to access lets say blackjack it is not on the games menu list.

The package contains the following games:
* aisleriot - different solitaire card games
* blackjack - the casino card game
* glchess - chess game with 3D graphics
* glines - color lines game, aka fiveormore
* gnect - four in a row game
* gnibbles - snake game, up to four players
* gnobots2 - improved old BSD robots game
* gnome-sudoku - Sudoku puzzle
* gnometris - Tetris, the popular Russian game
* gnomine - popular minesweeper puzzle game
* gnotravex - puzzle where you match tile edges together
* gnotski - klotski puzzle game
* gtali - sort of poker with dice and less money
* iagno - the popular Othello game
* mahjongg - classic Eastern tile game
* same-gnome - remove as many balls in as few moves as possible

from that list only the last 2 games appear on the menu.

Am I reading things wrongly assuming that by downloading AisleRiot Solitaire that the others will automatically load?

---

### Post by Roanoke on 2009-03-04
It might be that you need to add them manually (system->preferences->main menu) add them or run them from the terminal (<name of program> &). Though that is odd.

---

### Post by Scunnered on 2009-03-04
Roanoke

Thanks again.  Will have a look at what happens if I say select blackjack to load via add/remove.  It possibly might as you suggest be that they need individual attention.

The pool / billards game is a total loss as neither billiard-de or foobilliard work. Looks like my graphic card is too new for them.

Will return to drink as an alternative to games

---

### Post by LowSky on 2009-03-04
just remember you cant run Compiz with most graphical games... so turn it off and then try the game..

Also run the game from a terminal window and post any error the terminal reports... it will give us a better  idea of the issue

---

### Post by Scunnered on 2009-03-04
**LowSky**

Now you expose my ignorance ! I do not know how to run from the terminal. Roanoke gave me instructions to load the package but I then went to Applications > Games and selected the item.  

As to the Compiz question is this something that is automatically loaded or optional. I as far as I know did not load it but just in case will it show up on Synaptic as loaded.  When you say turn off is this a case of removal or is there a box that can be clicked on / off?

Thanks for your assistance

Edit.  Accessed Synaptic and found that it would appear that Compiz is loaded.  How do I deal with turning it off?  Would it effect things like viewing TV or streaming video?

---

### Post by Roanoke on 2009-03-04
Well, when you open a terminal (might as well just put a link in the top panel) you just type the name of the program to run it.
I don't recall if compiz is loaded automatically. Right click on your background ->change desktop background->Visual Effects, then ensure none is selected. Compiz is a suite of desktop effects that just adds eye candy. However, it is incompatible with apps that use OpenGL (such as blender). That may be your problem.

---

### Post by Scunnered on 2009-03-05
Roanoke

Thanks again for your input.

I applied the change that you advocated and tried again. Billard immediately displayed on the screen but disappeared equally as fast. There was no chance to see if there was any tool bar or help available.

Foobillard displayed but in only as far as it showed a table with a triangle of balls at one end and the white at the other.  There was a verticle line above the ball which I took to be where the ball would be struck but I was unable to change the direction of the line nor find a cue to work with.  Movement was possible but only in the positioning of the table.

I think that I shall abandon attempting to play billiards/pool and take up knitting. I think this will have a greater benefit as it is snowing here and a good wooly hat would not go wrong.

Once again thanks for everything

---

### Post by skymera on 2009-03-05
Sauerbraten is a good game that runs onm Ubuntu.

It's in the repositories :)

---

### Post by Scunnered on 2009-03-06
skymera

Thanks for your post. I had a look at your suggestion but I am not into shootemups. I will have a further search to see if any billard / pool games are available that will work with 8.10 64

---

