---
title: "Apache2, Shorewall, WPA security, and perl file execution problems."
date: 2011-07-21
forum: New to Ubuntu
---

### Post by OSad on 2011-07-21
First of all, apologies for the vague thread title. Alas, the character limitations cannot possibly begin to identify the problems I have.

I'm a new user to Ubuntu Server 10.04 {?} that was drawn to it for the sole reason of starting a private imageboard for some friends, with the purpose of backing up various images and links for future use. Ubuntu Server enticed me after the recommendation of said friends, for it served the purpose of hosting a dedicated web server without much processing strain or energy consumption. Also, I thought of it as a fun challenge to attempt to master this system that has absolutely no GUI to navigate with.

Going step by step and this may be a long read, but bear with me:

I formatted an old laptop and, following [this]("http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/") guide which seemed to be widely popular at the time of it's postation, I was able to get the core system installed flawlessly. I decided to ignore the fact that the guide had an outdated Ubuntu version, since I figured the core architecture couldn't have changed much.

To update the server, I needed to set up a wireless connection to my router, which has WAP2 security. However, I simply could not understand how to input my security key on the Ubuntu console, even by attempting to follow various guides. I opted for disabling security on my router and putting myself at risk for the opportunity of various leechers om-nom-noming my network while I attempted the rest of the server setup. Fair enough, if they screw something up, all I do is hit the reset button on the hardware and magically, everything was fine again. And so I command lined -sudo iwconfig essid and -sudo dhclient and suddenly, before I could say prickles, my server was updating and upgrading, as the guide stated.

After that, I installed the apache2 and mysql's alikes the guide demanded. The installation went smoothly, without any trouble. However, when it came to configuring the bighters, some problems started to arose. The first of them being in the part where the guider asks of me to change ServerTokens Full to ServerTokens Prod. That line simply did not exist on the apache2.conf file. I was shocked! Le gasp. ServerSignature also was not present, to my dismay. I opted for making the changes on the php.ini file and continue ignoring these steps, making a pass at them later.

After that, the guide suggested I installed a firewall called "Shorewall". I wasn't too concerned with security since, wel, my router is passwordless and all. But still, leaders shall lead. Successfully installing it, I proceeded to be dumbfounded by the following console command; 

-sudo cp /usr/share/doc/shorewall-common/examples/one-interface/* /etc/shorewall/

I attempted to recreate it various times, but would get an invalid command line every time I attempted so. Skipped, since we don't have enough skippings already. And again, I was forced to skip the next step, since the system was unable to find the "rules" file.

Blast it, let's just get this all out of the way, completely forfeit security for now and get this shank running. I attempted the input of the following commands;

sudo usermod -g www-data [YOUR USERNAME]
sudo chown -R www-data:www-data /var/www
sudo chmod -R 775 /var/www

While the first and third worked, the second did not, reporting an error message I cannot quite remember. Fair enough, I downloaded Firezilla and successfully connected to my server.

Another difficulty arose, however: I did not have, and still don't, have the blightest idea on how to run .pl files on a Ubuntu Server. Of course I went out in search of a guide. [This]("http://www.blog.highub.com/perl/install-configure-apache-localhost-perl-on-linux-ubuntu/"), guide. It seemed simple enough, simply yank the apache2.conf file out, make some changes to it, and shove it back in.

Using my uncanny abilities, I -sudo chmod'ed 777 my way into the Apache2 folder and acquired access to read, write and add files to that section. This is the part where I got all witty with myself, hihihihihi! Anyway, I successfully downloaded the perl addon for Apache, added the command lines with my server folder to it, which happens to be /var/www/cgi/, and closed it all up. However, attempting to access the files through a friend's PC or through a proxy, simply made me download the .pl file to my computer. Dumbfounding! I heard that the files are properly executed by running .cgi instead of .pl, but doing that just yielded me a 404. Disappointing! Before any of you ask, yes, other people can successfully enter my address and fuss about the server files. That's totally cool and edgy and dangerous, I know. Still, science knows no bounds.

So here I am. If you did not read any of that wall of text, and I don't blame you, I'll give a lowdown on my problems;

1.Could anyone give me concise instructions as to how I can input my WAP2 security key onto Ubuntu? Leaving it unlocked is making me all twitchy. 

2.Some of the lines and files previously mentioned for Apache2 seem to not work. Are they outdated or exist at all?

3.Shorewall is a 3-year-old girl. I cannot get it to work properly with that guide. Is there an updated version?

4.The mystery of the sudo chown -R www-data:www-data /var/www line! What does it do?! We could almost turn this into a sci-fi thriller.

5.Even though the lines are placed in the apache2.conf file, the .pl and .cgi interpreter do not seem to work. The server itself works, people can see it, and access it, but the server is not executing the .pl file for whatever reason. There are no error logs to show since it's not giving me an error, of course.

I'm sorry, since I know these have been asked thousands of times before. However, the random bits and pieces of knowledge I gather from around the intertubes are not solving my issues. I decided to tap from the fountain of knowledge itself.

And finally, if anyone is interested, [here is the imageboard files and scripts I am attempting to use]("http://wakaba.c3.cx/releases/kareha_3.1.4.zip"). I'm attempting Kareha because apparently, not only it's simpler, it also does not require a mysql backbone, which is less complications on my side. 

I eagerly await responses, and will standby. Thank you for your time!

---

### Post by uRock on 2011-07-21
Hello and welcome to Ubuntu Forums.

You may get better answers if you break up questions about different subjects and create separate posts in the proper sub-forums with the questions, such as Apache related questions in the [Server Platforms]("http://ubuntuforums.org/forumdisplay.php?f=339") section, Shorewall & WPA in the [Security Discussions]("http://ubuntuforums.org/forumdisplay.php?f=338") section.

Regards,
uRock

---

