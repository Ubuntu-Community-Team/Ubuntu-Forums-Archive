---
title: "Commands in Cario Launchers?"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by cre8ive65 on 2011-06-30
Hiya!
I just made my minecraft server (If your interested id be happy to white-list you to check it out before i make it public, it works with hacked clients as well) and i made a nifty little file on my desktop called RMS to start it. Its contents are:

```
cd /home/cre8ive65/.mcserver/
java -Xms1024M -Xmx1024M -jar minecraft_server.jar nogui

```

When i double click on the file on my desktop or in nautilus, Ubuntu asks me if i want to Run, Run in Terminal, or display its contents, i would normally click run in terminal, and inside the gnome terminal would by my minecraft console

Now here is my dilemma

I tried clicking and dragging the file i made onto my cario dock, but when i click on it, it skips the dialogue box asking me what i want to do with it, and displays the files contents in gedit

I tried making a custom launcher in cario and set the command to the same one in the file, no luck. I tried making the file a ".sh" and putting: 
```
sh /home/cre8ive65/Desktop/RMS.sh
``` 

in the command space and no avail. I set the command to: ```
java -Xms1024M -Xmx1024M -jar /home/cre8ive65/.mcserver/minecraft_server.jar nogui
``` 

but this makes a totally new server in my home folder! So how do i make a cario launcher to start my server!? Any help is much appreciated, Thank you!

---

### Post by jtarin on 2011-06-30
Instead of```
cd /home/cre8ive65/.mcserver/
java -Xms1024M -Xmx1024M -jar minecraft_server.jar nogui
```Try```
cd /home/cre8ive65/.mcserver/
./java -Xms1024M -Xmx1024M -jar minecraft_server.jar nogui
```

---

### Post by cre8ive65 on 2011-07-03
Thanks for the help, but i got the same problem
I tried setting that command in both Cario and in my File (I think the problem is the text field in Cario is a single line) I solved the problem by leaving my file as

```
cd /home/cre8ive65/.mcserver/
java -Xms1024M -Xmx1024M -jar minecraft_server.jar nogui
```

Only difference is that i set the command in Cario to

```
cd /home/cre8ive65/Desktop/ && ./Minecraft-Server
```

Now the terminal that would contain my server admin console was running in the background, I solved this by checking "Run in terminal" under "Extra Parameters"

Thank you very much for the help, and again if you would like to play on my server, pm me with your username, and I'll white list you and give you my ip

Cheers:)

---

