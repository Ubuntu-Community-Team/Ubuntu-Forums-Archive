---
title: "Can't play songs is terminal"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by Linyx on 2011-02-16
I am trying to play mp3-Songs in terminal, for that i had install XMMS, but when i run Command:-

```
play song.mp3
```

It returns:-

> play FAIL formats: no handler for file extension `mp3'

From the above error it seems that i am missing codecs, but i can run my musics through every GUI-Player,

Moreover i am able to run Music by mplayer in terminal but i want to use XXMS....

Any suggestions...?

---

### Post by AlphaLexman on 2011-02-16
Shouldn't the command be:
```
xmms --play song.mp3
```?

---

### Post by Linyx on 2011-02-16
> **AlphaLexman said:**
> Shouldn't the command be:
```
xmms --play song.mp3
```?

I don't think so, because the Terminal Output is:-
> xmms --play Dont_matter.mp3
No command 'xmms' found, did you mean:
 Command 'lmms' from package 'lmms' (universe)
 Command 'xmms2' from package 'xmms2-client-cli' (universe)
 Command 'xmds' from package 'xmds' (universe)
 Command 'xdms' from package 'xdms' (universe)
xmms: command not found


---

### Post by sydbat on 2011-02-16
> **Linyx said:**
> I don't think so, because the Terminal Output is:-The error gives you the answer - try xmms2.

---

### Post by AlphaLexman on 2011-02-16
> **Linyx said:**
> i had install XMMS, but i want to use XXMS....We may have a language barrier, but I will try to help.

I am not familiar with the executable **'play'**

Try these commands separately, ```
which play
``````
locate mpg123
``````
locate mpg321
```If you can confirm just one of the above two commands. Try that one from the terminal, for example:```
mpg123 Dont_matter.mp3
```

---

### Post by Linyx on 2011-02-16
OK, so now i had tried this command :-

```
xmms2 play song.mp3
```

it shows me the Output:-

> This program is deprecated and will be replaced by nyxmms2.
 Consider setting runnycli to 'true' in config file to get future behaviour
 (or set iknowoldcliisdeprecatedandwillgoaway to 'true' to hide this warning)
 The config file is located at:
    /home/assassin/.config/xmms2/clients/cli.conf


I done that & now when i try command:-
```
xmms2 play song.mp3
```

Nothing happens, Terminal isn't showing me any error neither it play song.....!

---

### Post by Linyx on 2011-02-16
@Alphalexman:-

mpg123 is another tool...I had Removed xmms2 and install mpg123,and it working well...thankx

---

### Post by AlphaLexman on 2011-02-16
> **Linyx said:**
> @Alphalexman:-

mpg123 is another tool...I had Removed xmms2 and install mpg123,and it working well...thankxYou're welcome. I believe xmms2 is actually a daemon that runs in the backgroud and needs a separate frontend to control it. Quite daunting imo to just play an mp3.

---

### Post by Linyx on 2011-02-16
> **AlphaLexman said:**
> You're welcome. I believe xmms2 is actually a daemon that runs in the backgroud and needs a separate frontend to control it. Quite daunting imo to just play an mp3.

Ok, so now i had type xxms2 in terminal> **Screen-Shot** & it shows me the Entering Section...Where i am able to enter Commands,

Anyway, Problem is Solved.

---

### Post by emazep on 2011-02-17
> **Linyx said:**
> I am trying to play mp3-Songs in terminal, for that i had install XMMS, but when i run Command:-

```
play song.mp3
```It returns:-



From the above error it seems that i am missing [FONT=Verdana]codecs[/FONT]...


Linyx, if you run [FONT=Courier New]play[/FONT] you're really calling [FONT=Courier New]sox[/FONT], not [FONT=Courier New]xmms[/FONT].
However, you were perfect right about the missing codec: just install [FONT=Courier New]libsox-fmt-mp3[FONT=Verdana] and you'll be able to play an mp3 through:[/FONT][/FONT]
```
play song.mp3
```Ciao!

---

### Post by Linyx on 2011-02-18
> **emazep said:**
> Linyx, if you run [FONT=Courier New]play[/FONT] you're really calling [FONT=Courier New]sox[/FONT], not [FONT=Courier New]xmms[/FONT].
However, you were perfect right about the missing codec: just install [FONT=Courier New]libsox-fmt-mp3[FONT=Verdana] and you'll be able to play an mp3 through:[/FONT][/FONT]
```
play song.mp3
```Ciao!

Nice suggestion, it worked !!

thanks:P

---

### Post by andrew.46 on 2011-02-18
> **Linyx said:**
> I am trying to play mp3-Songs in terminal, for that i had install XMMS, but when i run Command:-

```
play song.mp3
```



The play command is part of sox rather than xmms...

---

