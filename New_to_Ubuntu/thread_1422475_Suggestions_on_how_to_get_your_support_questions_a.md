---
title: "Suggestions on how to get your support questions answered as quickly as possible"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by undecim on 2010-03-05
When posting a question on the Ubuntu forums, there are some things you can do to make sure your question gets answered quickly.

[SIZE="3"]General Guidelines[/SIZE]
[LIST=1]
[*]**There are no stupid questions.** You're not a stupid person simply because you do not know how to do something, or do not have the answer to a question. Everyone was a green user at one point in time. :)
[*]**Use the forum search first.** Most problems have happened to at least one other person before, and have already been discussed in an existing thread. If you can find your solution this way, it will be much faster than waiting on someone else. The search box can be found in the upper-righthand corner of the page.
[*]**Post in the correct forum.** At the end of this post is a list of forums that you can post your questions or comments in. If you post in a forum that is not meant for your question, then it will have to be moved by a moderator to the correct forum, which make support take longer. If you accidentally post in the wrong forum, ask a moderator to move it for you rather than making a new post, or one of your posts will get deleted.
[*]**Make the title of your thread meaningful and concise.** For example, if you are having difficulty using your BroadCom card to connect to your wireless internet, the title "Cannot connect to wireless with BroadCom card" will attract people with experience with wireless internet and BroadCom cards. Titles like "Help me please!!!" or "I have a problem" may be overlooked by people who could otherwise help you.
[*]**Indicate your level of experience with Ubuntu and the topic of your problem.** If you are new to Ubuntu, mention that at the beginning of your post. There are often many ways to solve a problem, and knowing your level of expertise will help others suggest the method that is best for you.
[*]**Explain how you installed or are installing Ubuntu, and which version you are using.** There are many different flavors of Ubuntu, several ways to install it, and usually more than 2 release versions of Ubuntu currently supported. If you had Ubuntu pre-installed on your computer, say so. If you are using standard Ubuntu, say so. If you are using one of the flavors of Ubuntu with a different desktop envionment, say so. 
[*]**Provide information relevant to your problem.** Error messages usually contain valuable information, so include those in your post.

If the error message is contained in terminal output, copy and paste that output between BBCode [noparse]```
 and 
```[/noparse] tags to retain formatting and clarity. You can copy and paste by highlighting the terminal output with your mouse, right-click -> copy, and then pasting into your post with right-click -> paste. How to use BBCode code tags is detailed [here](https://ubuntuforums.org/showthread.php?p=12776168#post12776168)

If the error message shows in a GUI window, a screenshot is better than trying to transcribe the message by typing it. To take a screenshot of an active window in Ubuntu, press the Alt and PrtScn keys simultaneously. The screenshot will be saved to your Pictures folder, and can then be attached to your post using the paper-clip icon in the advanced message editor toolbar.

Please do not use off-site websites for any screenshots or images - the forum attachment facility suffices - and do not attach screenshots of terminal output as these are difficult to read.

If your problem is related to any specific hardware, (for example, wireless or video problems), then include a model number for that piece of hardware. If you don't know how to find your model number, look at the "Hardware Information" section below.
	
[*]**Use proper grammar and punctuation.** Most members of the forum won't get stuck up on grammar, spelling or punctuation, but grammar is still important when communicating your problem. This makes it easier for those on the receiving end of your message to understand what you meant, especially for those who are not native English speakers. At minimum you should mark the end of your sentences.
[*]**Don't ramble.** Some background information on your problem is necessary, but try to keep all the information in your post relevant to your problem.
[*]**Follow the Ubuntu Forums Code of Conduct.** [The UF Code of Conduct](http://ubuntuforums.org/misc.php?do=showrules) details the forum rules that all users must abide by. These rules can generally be summed up to one phrase: Be friendly to everyone. If you follow that one rule, there should be no problems. Section II of the Code of Conduct also gives some advice on asking for technical support.
[*]**Check back on your thread and answer any questions others have about your problem.** Sometimes more information will be required to fix your problem, and a forum member will respond to your thread with instructions on how to get that information. If you do not like to check back on the thread page, you can use the "Subscribe to this Thread" feature from the Thread Tools menu near the upper-lefthand corner of the page.
[*]**Let us know when it's fixed.** When your problem is solved, mark your thread  as [SOLVED] by using the Thread Tools menu near the upper-righthand corner of the page, and remember to thank those who helped fix your problem. This lets us know that we are doing some good with our time, and encourages us to keep at it.
[*]**Post only one thread on your topic.** Posting multiple threads dilutes community effort, and makes it more difficult for others to help.
[/LIST]

If you believe that you have been **cracked or otherwise attacked**, please read [this]("http://ubuntuforums.org/showthread.php?t=1897765") before posting.


[SIZE="3"]Hardware Information.[/SIZE]
Often times, it is helpful to include information about the hardware attached to your system. For example, if you are having graphical problems, information about your video card is helpful.

The quickest way to get your hardware information is by opening a terminal. In Ubuntu you can do that from the dash. In other flavors you can open the terminal from the applications menu, which varies from flavor to flavor. Alternatively you can use the keyboard shortcut Ctrl-Alt-t. From a terminal you can type and run commands that will give you information about your hardware.

For a comprehensive view of detailed information about your hardware, system settings and how it is configured, run the Ubuntu Forums 'system-info' script from the [UbuntuForums 'system-info']("https://github.com/UbuntuForums/system-info") GitHub page. It was written to help the Users of Ubuntu Forums to recommend informed solutions to Users needing help. This script has been tested to run and be safe on Desktop and Server Editions of Ubuntu, it's flavors of (Lubuntu, Xubuntu, Mate, etc), derivative distributions of Ubuntu, and varying architectures that Ubuntu can run on. The instructions to run it are in the README.MD file there, displayed on that page. The script will first preview information about your system in an on-screen display of a report. Do not post this on-screen information to the Forum. This is for your "Eyes Only." After that it will offer to upload a safe and sanitized version of that report to a pastebin for you, if that system has an internet connection. It does not, no problem. It creates a text file of that sanitized report in your Home directory, which you can later attach to your post as a text file.

To get information on your wireless card, please read this sticky - [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) . Follow the instructions there to download the wireless-info script and to run it. The sticky has a link at the bottom of the post to the github repo page for the wireless-info script, but here is the link anyway - [https://github.com/UbuntuForums/wireless-info](https://github.com/UbuntuForums/wireless-info) - which also has instructions. 

To find out what video card you have, copy and paste this command into the terminal. (If you like to use keyboard shortcuts to copy/paste, you will have to use Ctrl+Shift+V rather than Ctrl+V when pasting to the terminal)
```
lspci | grep -i VGA
```and press enter. The text displayed will include information about your video card including its manufacturer and model number.

To simply list all PCI cards (i.e. All the extra pieces of hardware attached to your system), use
```
lspci
```

You can get an exhaustive, detailed list of hardware on your computer. This requires doing things that need administrative privileges, so this command will have you type your password. When you type your password into a terminal, you will not see any characters, not even asterisks. This is perfectly normal and your password is typing just fine.
```
sudo lshw
```

Another utility that displays hardware information for your system is inxi. Install it from a terminal with the command:

```
sudo apt install inxi
```

Then run it with this command:

```
inxi -F
``` 

[SIZE="3"]The support forums[/SIZE]
There are several support forums where you can post your questions. Please post your question in only one forum. Double-posting is frowned upon and will usually result in one of your threads being locked. Most forums have "sticky" threads at the top of the list of threads. They contain useful information that may be relevant to your problem. Please see if you need to read any **before** posting.

[New to Ubuntu](https://ubuntuforums.org/forumdisplay.php?f=326) - The perfect place to post for your Ubuntu support if you are new to Linux.
[General Help](https://ubuntuforums.org/forumdisplay.php?f=331) - All your general support questions for Ubuntu, Kubuntu, Edubuntu, Xubuntu, Lubuntu, Ubuntu Mate, Ubuntu Budgie, Ubuntu Studio and Ubuntu Kylin.
[Installation & Upgrades](https://ubuntuforums.org/forumdisplay.php?f=333) - For questions about upgrading and installation of your new Ubuntu OS.
[Hardware](https://ubuntuforums.org/forumdisplay.php?f=332) - Problems getting your hardware to work with Ubuntu? Post your questions here.
[Desktop Environments](https://ubuntuforums.org/forumdisplay.php?f=329) - Support for your Ubuntu desktop. Including Gnome, KDE, XFCE, LXDE, LXQT, Budgie and Mate.
[Networking & Wireless](https://ubuntuforums.org/forumdisplay.php?f=336) - Having problems getting connected to the internet or getting your wireless card to work? Ask here.
[Multimedia Software](https://ubuntuforums.org/forumdisplay.php?f=334) - The place for your multimedia software questions: everything about using software for audio, video and image editing, display, or viewing and listening. 
[Security Discussions](https://ubuntuforums.org/forumdisplay.php?f=338) - Questions about security in Ubuntu and the official flavours.
[Virtualisation](https://ubuntuforums.org/forumdisplay.php?f=308) - For questions on virtualization software running Ubuntu, or the official flavours, as either host or guest.
[Server Platforms](https://ubuntuforums.org/forumdisplay.php?f=339) - Discussion regarding the Ubuntu Server Edition. For more information on the Ubuntu Server Team, please visit their wiki page or Launchpad page.
[Gaming & Leisure](https://ubuntuforums.org/forumdisplay.php?f=93) - A section for users who strive to play games on Ubuntu.
[Apple Hardware Users](https://ubuntuforums.org/forumdisplay.php?f=328) - Support for users who are using Apple Intel or PPC based systems with Ubuntu.


For a complete list of all the forums on this site, including non-support forums, go to the [UF index page.](https://ubuntuforums.org/forum.php/)


Also, a special thanks to matthew for stickying this post, and to aysiu, Sef, and 2hot6ft2 for helping improve it.


**Footnote**: this post originally had over 80 replies, but all these replies are over 10 years old. For historical reasons only they are visible in a separate thread here: [https://ubuntuforums.org/showthread.php?t=2472105](https://ubuntuforums.org/showthread.php?t=2472105)

---

