---
title: "Keyboard shortcut for ap that requires a terminal to run"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by crowhill on 2010-06-17
Hi there

I have MATLAB. I can start it from a terminal by cd'ing to its directory where I can execute the executable 'matlab'. In short, I can do this

/home/crowhill/programs/matlab/bin/matlab &

in a terminal (the & at the end gives me the command line back). This works fine. Now, I want to add a keyboard shortcut that executes this command for me. When I go to adding keyboard shortcuts somewhere in the menu and add the above command, it does no longer work. The MATLAB boot-window appears but then disappears again. MATLAB never starts. The problem seems to be that this command requires a terminal to run in. How do I modify the above command so that it executes in a terminal?

Thanks so much!

---

### Post by elysianfields44 on 2010-06-17
So did you make the shortcut command to be:

/home/crowhill/programs/matlab/bin/matlab

or something else? I just tried creating a keyboard shortcut the exact same way (for Wing IDE) and it works so I really don't think it has anything to do with whether you are running it in a terminal.

Could you also post the permissions on the matlab executable? cd to the bin directory and then do:

```

ls -alF | grep matlab

```

If it's not executable by everyone, you could try this:

```

cd /home/crowhill/programs/matlab/bin
sudo chmod 755 matlab

```

Alternatively, can you try making an application launcher on the panel and see if that works? (Right click top panel, Add to panel, Custom Application Launcher)

---

### Post by crowhill on 2010-06-18
The output of your command is

-rwxr-xr-x  1 crowhill crowhill  55271 2010-03-29 11:34 matlab*

When I use the launcher thingee in the panel (which is not what I want) and use

/home/crowhill/programs/matlab/bin/matlab

for the command, Matlab appears but after 1 second disappears again. It never starts.

Indeed, when adding a keyboard shortcut command I was using the command

/home/crowhill/programs/matlab/bin/matlab

or

/home/crowhill/programs/matlab/bin/matlab &

and neither works.

Andy ideas?

---

