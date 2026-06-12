---
title: "what are 3D drivers and how do i get them ?"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by f6e9a on 2010-10-09
ok i want to install steam on my computer 
which is only available for mac and windows but acording to this video [http://www.youtube.com/watch?v=Vxwnk33gxm0&feature=related](http://www.youtube.com/watch?v=Vxwnk33gxm0&feature=related)
i can get it but i dont understand the instructions in the description or wut is avi or Nvida

here is a copy of the instructions
1. You need all 3D drivers installed (Nvida,ATI and so on)
2.  Download [http://rapidshare.com/files/135850027...]("http://www.youtube.com/redirect?q=http%3A%2F%2Frapidshare.com%2Ffiles%2F135850027%2Fsteam-ubuntu_0.4.tar.gz.html&session_token=q509p1yhwFkj2rwjmkZv9oWtXpR8MTI4Njc0NzkyNQ%3D%3D")

3.  extract the archive with "tar xfvz steam-ubuntu_0.4.tar.gz" in your  terminal

4. Change to the directory where you extracted the  archive with "cd /whereyourfolderis/steam-ubuntu" in your terminal

5.  start the installation with "./steam-ubuntu.sh" in your terminal

6.  Follow the instructions (The installer is german... sorry for that! you  have to type in 1 and then press enter. I will make an english version  soon. But the gamelanguage is english don't worry)

7. Start steam  and install your game (it may take some time for steam to update)

8.  Play and have fun!

thanks for all the help,
f6e9a

---

### Post by Mark Phelps on 2010-10-09
You first need to find out what video card you're using.  Forcing the install of the wrong drivers will trash your display, forcing you to go into command mode to remove them.

To find out, open a terminal and enter "lspci" and look for a line containing VGA.  Post the results back here.

---

### Post by f6e9a on 2010-10-09
"00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)"

thats what it said!!


thanks for helping me in advance i feel really happy

---

### Post by BaffledMollusc on 2010-10-09
Okay, I'm not sure how much this will help you, but here are my thoughts.

The Steam client is not available for linux, nor are most of the games available from the Steam online store. So assuming that YouTube video isn't a fake, I assume they must be running the Steam client under WINE.

WINE is a linux program that allows you to run Windows software under linux. For some things it works well; for others not at all. So don't magically expect to do this and have Steam and all Steam apps work.

Now, 3D drivers. ATI and Nvidia are companies that produce graphics cards. You, however, appear to have the Intel 855GM chipset, which isn't a graphics card, but rather what's called "integrated graphics", a chip on your motherboard. It is nowhere near as powerful as a discrete graphics card and will struggle to run games well. On the plus side, I'm pretty sure the drivers for it are already installed - they should come with the basic installation of Ubuntu. On the minus side, I'm not sure if WINE supports Intel integrated graphics, or just ATI and Nvidia cards.

Sorry, that's the best I can do!

---

### Post by sandyd on 2010-10-09
> **BaffledMollusc said:**
> Okay, I'm not sure how much this will help you, but here are my thoughts.

The Steam client is not available for linux, nor are most of the games available from the Steam online store. So assuming that YouTube video isn't a fake, I assume they must be running the Steam client under WINE.

WINE is a linux program that allows you to run Windows software under linux. For some things it works well; for others not at all. So don't magically expect to do this and have Steam and all Steam apps work.

Now, 3D drivers. ATI and Nvidia are companies that produce graphics cards. You, however, appear to have the Intel 855GM chipset, which isn't a graphics card, but rather what's called "integrated graphics", a chip on your motherboard. It is nowhere near as powerful as a discrete graphics card and will struggle to run games well. On the plus side, I'm pretty sure the drivers for it are already installed - they should come with the basic installation of Ubuntu. On the minus side, I'm not sure if WINE supports Intel integrated graphics, or just ATI and Nvidia cards.

Sorry, that's the best I can do!
There was a leaked steam client for linux a while ago, everyone was harping on when we were actually going to get the official version....
and fyi, WINE supports intel cards, its just that they suck because they don't have dedicated GDDR
Theirs a few stores close to where I am that have the ones with dedicated video memory, those perform... ok, even though I would never use them to play games.

---

### Post by sandyd on 2010-10-09
> **f6e9a said:**
> ok i want to install steam on my computer 
which is only available for mac and windows but acording to this video [http://www.youtube.com/watch?v=Vxwnk33gxm0&feature=related](http://www.youtube.com/watch?v=Vxwnk33gxm0&feature=related)
i can get it but i dont understand the instructions in the description or wut is avi or Nvida

here is a copy of the instructions
1. You need all 3D drivers installed (Nvida,ATI and so on)
2.  Download [http://rapidshare.com/files/135850027...]("http://www.youtube.com/redirect?q=http%3A%2F%2Frapidshare.com%2Ffiles%2F135850027%2Fsteam-ubuntu_0.4.tar.gz.html&session_token=q509p1yhwFkj2rwjmkZv9oWtXpR8MTI4Njc0NzkyNQ%3D%3D")

3.  extract the archive with "tar xfvz steam-ubuntu_0.4.tar.gz" in your  terminal

4. Change to the directory where you extracted the  archive with "cd /whereyourfolderis/steam-ubuntu" in your terminal

5.  start the installation with "./steam-ubuntu.sh" in your terminal

6.  Follow the instructions (The installer is german... sorry for that! you  have to type in 1 and then press enter. I will make an english version  soon. But the gamelanguage is english don't worry)

7. Start steam  and install your game (it may take some time for steam to update)

8.  Play and have fun!

thanks for all the help,
f6e9a
you already have the latest 3d drivers installed, however I doubt that the card will be powerful enough to run any games.

---

