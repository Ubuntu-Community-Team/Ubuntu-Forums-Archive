---
title: "how to I add internet radio stations to Amarok 2.3?"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by Old Jimma on 2010-06-16
Hi Community:

I am using Amarok 2.3 and want to save my favorite internet radio stations so that I can play them when I want from Amarok.

I don't see how to do this with this version.

Can somebody provide guidance on how to get this done?

Thanks,
Phil SMith

ps. I've read some pretty flaming discussions about this and don't want to get into any finger pointing. I just want to learn how to use Amarok 2.3 to save my favorite URLs of streaming radio to play when I want. 

THanks,
Phil

---

### Post by Chesamo on 2010-06-16
Open the Playlists view and right-click on Radio Streams. Click "Add Radio Station". You'll have to get the exact URL of the stream, which you can get by opening the *.pls, *.asx or whatever file in Gedit.

---

### Post by Old Jimma on 2010-06-17
Hi Chesamo:

In my version of Amarok 2.3 there isn't an "add radio stream" under playlist.

I've attached a screenshot.

Could you tell me how to generate one?

ALso, where do I find the file that I open with gedit? I've got most of the URLs of radio stations that I want to listen to.

Thanks for your help, Chesamo.

Best regards,
Phil Smith
Duluth, GA

---

### Post by Chesamo on 2010-06-17
According to the Amarok documentation, you have to create a Saved playlist and add items to that.

As far as "getting the file", you should have downloaded a playlist file from the server, [from something like this web page](http://sublevel21.com/listen/). If you always just clicked "open", don't. Click "Save" and drop it in your Home folder or Desktop.

---

### Post by Old Jimma on 2010-06-17
Hi Chesamo:

I'm certain that this is pretty frustrating for you.

I cannot find any Amarok 2.3 documentation .... did a google and couldn't find it.

Also, I've added a saved playlist and named it "Radio Stations" but can see how to add URLs to it.

Thanks,
Phil

---

### Post by mc4man on 2010-06-17
Note that I think amarok2 on gnome is pretty awful but you can add radio stations in a couple of ways.

By far the easiest would be to have them as .m3u's, .pls's, ect.

If so then put them all in a folder somewhere, then go - 

settings -> configure amarok -> collection, browse to the folder you put them in and add to collection.
(screen 1

You'll then find them under ' playlist files on disk'

If you just have a url, a couple of ways - the easiest I see is - 

Clear your playlist so it's empty, then playlist -> add stream and paste your url in and click ok. (screen 2

Then go playlist -> 'export playlist as' - name it and save to the folder where you're keeping radio stations as mentioned above.
screen 3

---

### Post by Old Jimma on 2010-06-30
Folks:

Mc4man suggested 2 different ways of adding radio streams to Amarok 2.3. The second method worked for me. Here are the steps and some advice.

[LIST=1]
[*]Clear your playlist so it's empty, then playlist -> add stream and paste your url in and click ok.
[*]Then go playlist -> 'export playlist as' - name it and save to the folder where you're keeping radio stations as mentioned above.
[/LIST]

After you've done step 2, be patient it may take a minute for Amarok to realize that you've got a saved playlist and list it under 'saved playlists."

I hope this helps!

All the credit goes to mc4man.

Phil Smith
Duluth, GA
:guitar:

---

