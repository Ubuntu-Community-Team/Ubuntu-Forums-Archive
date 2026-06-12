---
title: "giganews"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by shadowlands on 2009-06-02
I have questions: I load uphellanzb and lottanzb.  I have giganews, but how do I search and down load items?

---

### Post by Lantash on 2009-06-03
There are plenty of Usenet search engines out there that let you download the corresponding NZB file when you've found something. This file can then be opened using LottaNZB in order to start the download. There are free sites such as [http://www.binsearch.info/](http://www.binsearch.info/) and some of them aren't but might provide more functionality such as [http://nzbmatrix.com/](http://nzbmatrix.com/) or [http://v3.newzbin.com/](http://v3.newzbin.com/).

---

### Post by shadowlands on 2009-06-03
You are great!  Thanks > **Lantash said:**
> There are plenty of Usenet search engines out there that let you download the corresponding NZB file when you've found something. This file can then be opened using LottaNZB in order to start the download. There are free sites such as [http://www.binsearch.info/](http://www.binsearch.info/) and some of them need aren't but might provide more functionality such as [http://nzbmatrix.com/](http://nzbmatrix.com/) or [http://v3.newzbin.com/](http://v3.newzbin.com/).

---

### Post by shadowlands on 2009-06-03
Newzbin says I need an invite.  anyone willing to help me with Giganews. Hey thewy give a 10 dollar credit to the person who refered you and I cancled mine last night until I have a better understanding of the system so I do not waste money.  But if I can get some one on one I will rejoin giganews and tell who sent me their way so they can get the credit.

---

### Post by mangurt on 2009-06-03
Well, lets see here.  Newsbin is a "pay for use site".  I don't know if you will be able to use that function without a subscription.  As for giganews and the like, I can give you some "one on one" help.  Send me a pm and I will walk you through it.

---

### Post by shadowlands on 2009-06-03
great. I do not mind paying to use the service.  > **mangurt said:**
> Well, lets see here.  Newsbin is a "pay for use site".  I don't know if you will be able to use that function without a subscription.  As for giganews and the like, I can give you some "one on one" help.  Send me a pm and I will walk you through it.

---

### Post by shadowlands on 2009-06-03
Looks like the cancellate did not go through so I can not give anyone the 10.00 dollar credit.


Sorry about that.

Did any one get a sentaxt error when they tried to work hellanzb?

Is this still a good guide: [http://jamiedumbill.com/index.php?page=39?](http://jamiedumbill.com/index.php?page=39?)

---

### Post by mangurt on 2009-06-03
If you are getting a syntx error with hellanzb, it most likely means you do not have the conf file set up correctly.  Did you edit that file?

---

### Post by shadowlands on 2009-06-03
no, i did not edit the file. Thanks, I will look at threads on how to edit the file.

---

### Post by mangurt on 2009-06-03
in terminal
[HTML]sudo gedit /usr/bin/hellanzb.conf[/HTML]

That will bring up the hellanzb configure file.  The file is pretty straight forward.  Scroll down until you see "change me", that's where you can change information.  Make sure you have the single quote mark ' in front of and behind what you want to fill in (I learned this from experience).
When you get to the newsgroup information, it should be 'news.giganews.com:119'
fill in your user name at the user name part, and password at password (include the ' before and after)
Connections=10
SSL=False

Further down the config file, you will see where hellanzb looks for nzb files, you can change this to whatever folder you want (I default mine to 'Documents'
completed filed 'Videos'

last but not least, look at the extract files='True'
and rar='/usr/ect/unrar'
(if you do not have unrar)
[HTML]sudo apt-get install unrar[/HTML]

Save the config file and close out gedit.  In terminal type hellanzb
You should see hellanzb running, waiting for an NZB file.  Grab a .nzb file from one of sites mentioned before, and see if hellanzb fires up.

To stop hellanzb, use the Ctrl + C

Hope that helps.

---

### Post by Lantash on 2009-06-03
With LottaNZB, you don't need to edit the configuration file by hand: LottaNZB does this for you. Using LottaNZB, the HellaNZB configuration file that is being used is ~/.lottanzb/hellanzb.conf (this directory is hidden) and not /usr/bin/hellanzb.conf. If it says that there is a syntax error you might want to reset the configuration by removing the hidden .lottanzb directory. However, I've never seen that LottaNZB created an invalid configuration file. LottaNZB tries to import existing HellaNZB configurations like /etc/hellanzb.conf. It seems more likely that the syntax error is in this file. You could try to rename it temporarily: 'sudo mv /etc/hellanzb.conf /etc/hellanzb.conf~'

Hope this helps! Send me a private message if you'd like a Newzbin invitation.

---

### Post by shadowlands on 2009-06-03
Dang, you are good is there a way to send you a virtual rose. Thank you so much for your help.

---

### Post by Lantash on 2009-06-03
Don't mention it. ^^

As I said, you can get an invitation to newzbin.com by sending your mail address to me as a personal message: [http://ubuntuforums.org/private.php?do=newpm](http://ubuntuforums.org/private.php?do=newpm) Of course you won't be obligated to actually buy Premium credits.

Did deleting the .lottanzb directory or renaming the /etc/hellanzb.conf file fix the problem?

---

### Post by shadowlands on 2009-06-03
I will let you know later tonight. I have been working on this during breaks at work and at lunch.  It keeps me out of office politics. Sometimes it is god to be dumb to the stuff going on around you.

---

### Post by shadowlands on 2009-06-03
my file is empty.  How do I delete the lottabin directory?
> **mangurt said:**
> in terminal
[HTML]sudo gedit /usr/bin/hellanzb.conf[/HTML]

That will bring up the hellanzb configure file.  The file is pretty straight forward.  Scroll down until you see "change me", that's where you can change information.  Make sure you have the single quote mark ' in front of and behind what you want to fill in (I learned this from experience).
When you get to the newsgroup information, it should be 'news.giganews.com:119'
fill in your user name at the user name part, and password at password (include the ' before and after)
Connections=10
SSL=False

Further down the config file, you will see where hellanzb looks for nzb files, you can change this to whatever folder you want (I default mine to 'Documents'
completed filed 'Videos'

last but not least, look at the extract files='True'
and rar='/usr/ect/unrar'
(if you do not have unrar)
[HTML]sudo apt-get install unrar[/HTML]

Save the config file and close out gedit.  In terminal type hellanzb
You should see hellanzb running, waiting for an NZB file.  Grab a .nzb file from one of sites mentioned before, and see if hellanzb fires up.

To stop hellanzb, use the Ctrl + C

Hope that helps.

---

### Post by shadowlands on 2009-06-03
How do I perform the action you recommended?  > **Lantash said:**
> Don't mention it. ^^

As I said, you can get an invitation to newzbin.com by sending your mail address to me as a personal message: [http://ubuntuforums.org/private.php?do=newpm](http://ubuntuforums.org/private.php?do=newpm) Of course you won't be obligated to actually buy Premium credits.

Did deleting the .lottanzb directory or renaming the /etc/hellanzb.conf file fix the problem?

---

### Post by click4851 on 2009-06-03
I like Newzleech, for my newsgroup searches

[http://www.newzleech.com/](http://www.newzleech.com/)

---

### Post by shadowlands on 2009-06-03
bump

---

### Post by mangurt on 2009-06-03
If you want to send a private message, click on the link in that post, and then type in the name of the person you want to send a PM to (ie lantash) and away you go.

I take it you did not get hellanzb working.  It took me a long, long time to figure it out.  I actually used sabnzbd for the longest time (interfaces with your default web browser), and with Jaunty it's super easy to install

```
sudo apt-get install sabnzbdplus
```
```
sudo apt-get install sabnzbdplus-theme-smpl
```
```
sudo apt-get install sabnzbdplus-theme-iphone
```
[HTML]sudo apt-get install sabnzbdplus-theme-plush[/HTML][HTML][/HTML]

After everything's installed
```
sabnzbdplus
```

And you can use the web interface to set everything up.

If you are not running Jaunty, there's a pretty good guide at [HTML]www.sabnzbd.org[/HTML]

Hope that helps

---

### Post by Lantash on 2009-06-04
SABnzbd is fine too, of course.

You can delete the ".lottanzb" directory in your home directory either by making it visible using Ctrl-H and deleting it or by running "rm -R ~/.lottanzb" in a terminal. I'm not sure if this will actually fix the problem because LottaNZB usually doesn't create invalid configuration files. You can prevent the existing configuration in /etc from being seen by LottaNZB by running "sudo mv /etc/hellanzb.conf /etc/hellanzb.conf~". May be that helps.

If this doesn't fix the problem when you run LottaNZB again, would you mind sending me the content of the hellanzb.conf file in .lottanzb in a private message, so I can figure out what the problem is?

---

### Post by shadowlands on 2009-06-04
I was told ther are no files in that directory after I ran the suggested command.> **Lantash said:**
> With LottaNZB, you don't need to edit the configuration file by hand: LottaNZB does this for you. Using LottaNZB, the HellaNZB configuration file that is being used is ~/.lottanzb/hellanzb.conf (this directory is hidden) and not /usr/bin/hellanzb.conf. If it says that there is a syntax error you might want to reset the configuration by removing the hidden .lottanzb directory. However, I've never seen that LottaNZB created an invalid configuration file. LottaNZB tries to import existing HellaNZB configurations like /etc/hellanzb.conf. It seems more likely that the syntax error is in this file. You could try to rename it temporarily: 'sudo mv /etc/hellanzb.conf /etc/hellanzb.conf~'

Hope this helps! Send me a private message if you'd like a Newzbin invitation.

---

### Post by Lantash on 2009-06-04
You ran both commands and you still can't launch LottaNZB?

---

### Post by shadowlands on 2009-06-04
thanks after the last command a new screen poped up stating that WARNING
No Usenet server defined, please check Config-->Servers


What does this mean and how do I fix it? > **mangurt said:**
> If you want to send a private message, click on the link in that post, and then type in the name of the person you want to send a PM to (ie lantash) and away you go.

I take it you did not get hellanzb working.  It took me a long, long time to figure it out.  I actually used sabnzbd for the longest time (interfaces with your default web browser), and with Jaunty it's super easy to install

```
sudo apt-get install sabnzbdplus
```
```
sudo apt-get install sabnzbdplus-theme-smpl
```
```
sudo apt-get install sabnzbdplus-theme-iphone
```
[HTML]sudo apt-get install sabnzbdplus-theme-plush[/HTML][HTML][/HTML]

After everything's installed
```
sabnzbdplus
```

And you can use the web interface to set everything up.

If you are not running Jaunty, there's a pretty good guide at [HTML]www.sabnzbd.org[/HTML]

Hope that helps

---

### Post by Lantash on 2009-06-04
Ah, you were referring to SABnzbd? The above commands didn't have anything to do with SABnzbd. In this case, you can manage your downloads in your browser. If running 'sabnzdb' didn't bring up Firefox, you will need to open the URL [http://localhost:8080/sabnzbd/](http://localhost:8080/sabnzbd/)

In the "Config" tab, you will need to choose "Server" and insert the necessary information.

---

### Post by shadowlands on 2009-06-04
yea refering to the new program.

what does this mean? "Last warnings (clear)
2009-06-04 08:06:30,258 WARNING [downloader] No active primary servers defined, will not download!
2009-06-04 08:10:30,808 WARNING [interface] API Key missing, please enter the api key from config>general into your 3rd party program:
2009-06-04 08:15:30,808 WARNING [interface] API Key missing, please enter the api key from config>general into your 3rd party program:
2009-06-04 08:20:30,808 WARNING [interface] API Key missing, please enter the api key from config>general into your 3rd party program:
2009-06-04 08:24:21,066 ERROR [sabnzbd.misc] Error getting url [http://www.giganews.com](http://www.giganews.com)
2009-06-04 10:11:16,022 WARNING [interface] API Key missing, please enter the api key from config>general into your 3rd party program:"> **Lantash said:**
> Ah, you were referring to SABnzbd? The above commands didn't have anything to do with SABnzbd. In this case, you can manage your downloads in your browser. If running 'sabnzdb' didn't bring up Firefox, you will need to open the URL [http://localhost:8080/sabnzbd/](http://localhost:8080/sabnzbd/)

In the "Config" tab, you will need to choose "Server" and insert the necessary information.

---

### Post by shadowlands on 2009-06-04
The link you gave open up the page that opened up after I ran the last command given by the most wonderful mangurt:KS:KS

---

### Post by shadowlands on 2009-06-04
Hey there are no ways to say thanks on this page so I gve all who have helped me Gold stars :KS:KS:KS:KS and a pop corn treat:popcorn::popcorn::popcorn::popcorn:.

---

### Post by Lantash on 2009-06-04
I guess this is because you didn't enter the right URL: Have a look at the Giganews FAQ: [http://www.giganews.com/faq.html#q5.5](http://www.giganews.com/faq.html#q5.5) The URL should be news.giganews.com

It's always a good idea to look for answers on your own first. Such FAQs and Google are likely to bring you on the right track and if not you are always free to ask in this forum.

---

### Post by shadowlands on 2009-06-04
Thanks. I guess I should try to be a bot more clear. I was asking if I had set up the SABnbd correctly.  I was pleased that the link give open up the page for SABndb that opened up when I ran the last command in the set of instructions.  

I was wondering why the page gave me an error message.  I am on their message board now reading information.  I am more of an end user than s build of programs so some of this is just not code but Greek as well. I see it read it and sit still makes no sense, but i refuse to o back to to using screw-me-gates products so I have a lot of terms to learn and z lot of reading a head of me.

---

### Post by mangurt on 2009-06-04
> **shadowlands said:**
> The link you gave open up the page that opened up after I ran the last command given by the most wonderful mangurt:KS:KS

You're quite welcome.  I don't know how many times I was hitting my head against the wall trying to figure it out.  I just like to spread the wealth when it comes to answering questions in this area.

Now that you have a nzb program going, have fun looking around.  Newsgroups was the way for me when I was deployed in Iraq :)

---

