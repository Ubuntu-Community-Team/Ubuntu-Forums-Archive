---
title: "Remotly control banshee"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by epqr on 2009-05-14
First off, I ahve no idea were to post this. Im sorry if this is the wrong section.

So; Im looking for a way to control my banshee music player remotely, and if possible from my ipod (it has wifi + web-browser). I search around and found [This]("http://markmail.org/message/puwtnkdzf7vv3sgx"). They i saw it was an written in C#, and i was a little confused (correct me if I'm wrong but isn't C# a Windows-only program?). I got even more confused when I found out it was a .exe file. 

Anyone that have tried this, or want to help me get it working? 

Or do anyone have another solution for remotely controlling banshee?

---

### Post by iswm on 2009-06-03
Check out Mono. It's casically an open source .NET implementation (including C# compiler, CLR, etc) for *nix and windows. Banshee is a C# app for Mono. The app you found is also a Mono app written in C#, so you can just use mono to invoke the .exe and you'll be good to go!

I haven't tried this particular program yet, but I'm looking for the same thing you are. I'll report back after I give it a try.

Update:
So I've gone ahead and given the program a try. Long story short is that it doesn't work with the current version of Banshee. The good news is that it looks fairly straight forward to get it working with Banshee's current DBus interfaces. I'll post another update after I've gotten it working with links to the new source and executable.

---

