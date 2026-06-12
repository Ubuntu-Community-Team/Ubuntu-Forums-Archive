---
title: "How to use SPHINX2 (speech recogn) with ALSA ?"
date: 2010-10-01
forum: New to Ubuntu
---

### Post by honeybear on 2010-10-01
Hello,

I have a usb mic at hw:1, and would like to use SPHINX with ALSA with it

here is the regular command of sphinx:

```
 /usr/bin/sphinx2-continuous -live TRUE -ctloffset 0 -ctlcount 100000000 -cepdir /usr/share/sphinx2/model/lm/turtle/ctl -datadir /usr/share/sphinx2/model/lm/turtle/ctl -agcemax TRUE -langwt 6.5 -fwdflatlw 8.5 -rescorelw 9.5 -ugwt 0.5 -fillpen 1e-10 -silpen 0.005 -inspen 0.65 -top 1 -topsenfrm 3 -topsenthresh -70000 -beam 2e-06 -npbeam 2e-06 -lpbeam 2e-05 -lponlybeam 0.0005 -nwbeam 0.0005 -fwdflat FALSE -fwdflatbeam 1e-08 -fwdflatnwbeam 0.0003 -bestpath TRUE -kbdumpdir /usr/share/sphinx2 -lmfn /usr/share/sphinx2/model/lm/turtle/turtle.lm -dictfn /usr/share/sphinx2/model/lm/turtle/turtle.dic -ndictfn /usr/share/sphinx2/model/hmm/6k/noisedict -phnfn /usr/share/sphinx2/model/hmm/6k/phone -mapfn /usr/share/sphinx2/model/hmm/6k/map -hmmdir /usr/share/sphinx2/model/hmm/6k -hmmdirlist /usr/share/sphinx2/model/hmm/6k -8bsen TRUE -sendumpfn /usr/share/sphinx2/model/hmm/6k/sendump -cbdir /usr/share/sphinx2/model/hmm/6k

```



 quote from web:
> 

I use sphinx2 and have a rather poorly coded, perl-based, voice
control system for my computer. The thing about it is that, from their
website, you can compiles a list of words/phrases that you want your
program to recognize, which means that once I came up with a suitably
diverse set of keywords ("play music" vs "stop noise", with "fast
forward" "rewind" etc.) the recognition is almost 100%.

It is rather convenient to be able to keep my hands on the keyboard
typing whatever it is that I am working on and start XMMS using my
voice.

(Also coded in keywords to run fetchmail and have an interactive
'biff' =) )

For those interested, possibly the best way to learn to use sphinx2 is
to go through the docs and look at the sample scripts. There's no
other was for me figure out the 967-character-long command+options
that is needed for my script.

Best,

W 


---

