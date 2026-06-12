---
title: "Slow internet speed only on terminal, Ubuntu 16.04"
date: 2018-02-18
forum: Networking &amp; Wireless
---

### Post by inv3nt0r on 2018-02-18
I have serious issue with Internet speed on my terminal. I have ASUS FX-553VD-DM483 laptop, and I have Windows 10 and Ubuntu and several Linux Distributions multiple booted. I am getting vert slow internet speed in the terminal. WHenever I try to install any software/package with apt-get install command or do any apt-get u Thread: Blurry screen and lots of eye strain pdate, the internet speed is very slow like about 20 KB/s while my internet speed is 10 Mbps. On browser it shows more than 8 Mbps but on terminal it just sucks while downloading anything. Screenshots are attached. 


[https://i.stack.imgur.com/afq3O.png](https://i.stack.imgur.com/afq3O.png)


Actual Speed on browser
[https://i.stack.imgur.com/XsaSz.png](https://i.stack.imgur.com/XsaSz.png)


I saw [this post]("https://askubuntu.com/questions/139187/wi-fi-internet-speed-for-terminal-is-slow-internet-speed-on-web-browser-is-fast") of the same problem but it suggests to change the server to the best server. I have a personal computer on the same network which gives more than 1 MBPS speed on every terminal operation from the same Indian servers. So the problem lies in my laptop ubuntu itself. I thought of drivers issue but if it was a drivers issue then browsers might have given slow speed, but browsers giving considerable amount of speed and all other applications like Tixati and torrent giving full speed except terminal. Please help!


Note: I tried with both Wifi and Wired with my lapi, same problems occurs with both.

---

### Post by DuckHook on 2018-02-18
Please don't post large graphics to the forums. This is very problematic for helpers with low speeds, who are on limited data plans, or are viewing from smartphones or small screens. It is also unnecessary to post whole screenshots in most cases anyway. Terminal output can be highlighted with the mouse, copied with a right click and pasted into the posting box between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar. We can take your word for the throughput you are getting on a speed test.

If you must post resource-hogging images, please post them as attachments using the paperclip icon in the *Adv Reply* toolbar.

I note a few things about your problem. Your slow speeds seem to be confined to uses of *apt*. Moreover, you mention Indian servers which implies that your geographical location is India, yet your system update source is pointed to an ftp server in some university in Taiwan. This is almost certainly the cause of your problem. You should be using a server that is much closer to your actual locale.

Do: Settings &#8594; Software & Updates &#8594; Download from: &#8594; Other &#8594; Select Best Server
Ubuntu will go through a process of testing server response from various mirrors. I don't know the various mirrors in your part of the world, but the result should be a mirror in India. If, for some reason, it still returns this oddball server in Taiwan, then ignore the result and choose a mirror close to home. You can test out various mirrors this way until you find one that gives you decent throughput.

As an aside, I also notice that you have may have activated the root account. If so, this is neither required, nor is it a good idea. Forgetfully operating as root can get you into a lot of trouble. Better to leave root disabled and use *sudo* as Ubuntu is designed to do.

---

