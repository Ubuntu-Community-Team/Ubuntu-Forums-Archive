---
title: "Live radio streaming"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by snowflake.nz on 2010-01-02
I would like to stream 2 radio stations. I just can't get them to work.
The urls are

[http://www.kfm.co.za/kinteractive/streaming/player.asp](http://www.kfm.co.za/kinteractive/streaming/player.asp)

and

[http://www.antfarm.co.za/clients/rsg/rsg_22.asx](http://www.antfarm.co.za/clients/rsg/rsg_22.asx)

I'm having trouble loading them.

---

### Post by pastalavista on 2010-01-02
Have you installed the restricted-extras package in the third party repositories?
If you have, try installing the VLC Media Player from the Software Center. If not, open System--> Administration--> Software Sources and do so.

---

### Post by rovinsan on 2010-01-02
> **snowflake.nz said:**
> I would like to stream 2 radio stations. I just can't get them to work.
The urls are

[http://www.kfm.co.za/kinteractive/streaming/player.asp](http://www.kfm.co.za/kinteractive/streaming/player.asp)

and

[http://www.antfarm.co.za/clients/rsg/rsg_22.asx](http://www.antfarm.co.za/clients/rsg/rsg_22.asx)

I'm having trouble loading them.
I think It's a browser problem.
What is your browser?

---

### Post by snowflake.nz on 2010-01-02
Pastalavista - All the restricted-extras are installed as far as I know. I'm not sure if there are any if I'm missing. I'm really new to this.

Rovinsan - I'm using FF3.5 but the urls work fine in FF, it's just that I don't want another FF window open - it slows my FF down

---

### Post by rovinsan on 2010-01-02
> **snowflake.nz said:**
> Pastalavista - All the restricted-extras are installed as far as I know. I'm not sure if there are any if I'm missing. I'm really new to this.

Rovinsan - I'm using FF3.5 but the urls work fine in FF, it's just that I don't want another FF window open - it slows my FF down
There are mainly 2 possibilities

1. Audio :- 
Check your audio is working properly...

2.Browser :- 
a) Update your Firefox. Help-> Check for updates. Then restart your browser.
b) Chose another browser, Epiphany. sudo apt-get install epiphany-browser

Then run the url in browser. :)

---

### Post by snowflake.nz on 2010-01-02
This is now solved. I just restarted my laptop and it resolved itself. 
Working beautifully now.
Thanks for all the suggestions guys. 
Update manager and a restart did the trick.

:KS

---

