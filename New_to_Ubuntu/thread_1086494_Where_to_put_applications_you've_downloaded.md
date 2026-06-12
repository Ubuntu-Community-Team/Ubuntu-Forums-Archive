---
title: "Where to put applications you've downloaded?"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by lone_wolfII on 2009-03-04
I've downloaded applications like Google Ocean and Vuze but I'm not sure where the best place is to put the contents of the extracted archive. 

So, what's the equivalent of the "Program Files" folder on systems like Windows XP?

---

### Post by ad_267 on 2009-03-04
/opt is usually where you install applications like that. I think /usr/local is another option but I'd usually go with /opt.

There isn't really an equivalent of "Program Files", due to the way file system splits up different parts of applications into different areas, eg libraries, configuration files, binary executables, data all go into different places. Windows does this too to some extent, often bits of applications like dlls end up in places other than in Program Files. If you're interested to learn about the file system layout a good place to start is here: [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by jaminux on 2009-03-04
The management of programs is done a little differently in Ubuntu (and Linux in general) compared to Windows.

The main way people install packages (programs) is through something called a repository. A repository is basically an online list of good reliable software tested software that is available to you. This is by far the fastest, most reliable and easiest way of getting programs and is one of the major pros of Linux over Windows.

For Debian based systems (Ubuntu being one), the nearest equivalent to a .exe file is a .deb file, if you can find one of these this is the next best alternative.

There is a third option, compiling from source, but that is much beyond you at this point. Although, you should remember it exists in case you want to do it later. That is what needs to be done with those archives, and is probably too difficult for you.

Luckily those two programs are available in the repositories for you, so you can quickly download them and they will be installed nice and easily.

There is an easier way (add/remove programs) to use the repositories than the one I am about to show you, but it is not that much easier to justify using it. You will benefit a lot more in the long run by learning how to use the one I am referring to. 

So here we go:

1) Go to System > Administration > Synaptic Package Manager. Enter your password when it prompts you, then maximize the window.

2) Click the big button that says search at the top of the screen and search for google earth (oceans is part of earth). a package for google earth will appear in the list below the button.

3) Right click the package and press mark for installation.

4) Use the big button again and search for vuze. Mark it for installation like you did for google earth.

5) To the left of the search button is a button called apply. Click it and it will download and install the programs for you.

6) Close the Synaptic. You should now be able to access your programs through the applications menu.

Not all packages are in the Synaptic, but the vast majority are. If only Windows had something like this and there would not be so much malware about...

---

