---
title: "help creating live usb"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by RhettJohnson on 2009-06-20
All,
I would like to make a live ubuntu usb key for an eeepc 900a.

I tried following the directions for installing the ubuntu netbook remix (UNR) using the command line directions and the utility flashnul. I don't read Russian and there are no English instructions. When I type the command flashnul-p all drives including the F:\ drive is listed. I assume that if Vista recognizes the drive as F:\ then this utility does as well. But, when I type the following command.
Instructions say type this:
flashnul <number obtained in prior step> -L \path\to\downloaded.img
So, I type this:
flashnul F:\ -L C:\Users\folder\folder\ubuntu-9.04-netbook-remix-i386.img
I get an error that says the drive is not ready. Any ideas for what is wrong here?

I would love to use the directions for the loader but they are for win32, I have Vista Business which is Win64 and I get an error that some dll is missing. So, if your advice is to do that please include directions for locating and installing the dll. I am very new to both Vista and Linux so assume I know nothing. i.e. If you want me to run something from the command line, you better tell me how to get to the command line. (I figured out how to do that, but you get the idea.)

Thanks in advance,
Rhett

---

### Post by shifty_powers on 2009-06-20
so you have ubuntu already installed?

then you can just use unetbootin, which should be in your admin menu...

---

### Post by t0p on 2009-06-20
You can download UNR [here]("http://www.ubuntu.com/getubuntu/download-netbook") - it comes as an IMG file that can be put onto a usb stick directly.  Instructions (in English) are [here]("https://help.ubuntu.com/community/Installation/FromImgFiles").

---

### Post by RhettJohnson on 2009-06-20
I do not have Ubuntu installed I have only downloaded the UNR. I am working on a Windows Vista Business box.

Unfortunately t0P the link you provided are the destructions I have been following. I have downloaded the UNR and it is sitting in this filepath - C:\Users\FolderNamehere\foldernameheretoo\ubunutu-9.04-netbook-remix-i386.img I obtained the path by right clicking on the address bar and then added the file name.

The GUI directions fail because launchpad is win32, I have Vista business (wrong or no dll for win64). The command line directions fail because I cannot seem to figure out how to get flashnul to recognize the above file path.

Any advice?

---

### Post by RhettJohnson on 2009-06-20
I don't have ubuntu installed - I am working in Windows Vista Business desktop. I am only have this desktop to work with to create the ubuntu live USB key for my eeePC. If I could get ubuntu installed I would work with it.

---

