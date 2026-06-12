---
title: "Installing 32-bit deb.sh file in a 64-bit system"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by seventhsamurai on 2010-09-09
Hi Guys

So I have this Lexmark X2630 Printer/Scanner combo which I am trying to install on a system running 64-bit Ubuntu 10.04.

I downloaded the linux driver from the Lexmark website. They only have a 32-bit driver and nothing for 64-bit. Also the file extension is something i haven't quite seen before. The filename is: lexmark-inkjet-08-driver-1.0-1.i386.deb.sh

I did a little reading online, tried to install it using the dpkg --force-architecture method, which in turn gave me an error saying that it is not a valid debian file.

Using sudo sh, I am able to start the installer, but it fails halfway, obviously because of my systems 64 bit architecture.

What do I do to install this. A friend had done it for me before on another machine, but I dont remember how he did it, and I can't get a hold of him. I'd appreciate your help.

---

### Post by 101011010010 on 2010-09-09
Hello.
Have you tried "getlibs". Have a look at this post hopefully it will help.

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by JohnHeikkila on 2010-09-09
Maybe it's just a name and is a bash script.
You could try running it with terminal
./lexmark-inkjet-08-driver-1.0-1.i386.deb.sh

---

### Post by seventhsamurai on 2010-09-09
Im unable to install using getlibs. its the .sh at the end of the file thats throwing everything off. its not a regular .deb file, so a lot of solutions offered online arent working. oh i am so frustrated.

---

### Post by seventhsamurai on 2010-09-09
> **JohnHeikkila said:**
> Maybe it's just a name and is a bash script.
You could try running it with terminal
./lexmark-inkjet-08-driver-1.0-1.i386.deb.sh

The above would work, but its a 32 bit file which I am trying to install on a 64 bit system. how do you force architecture with the above method?

---

### Post by JohnHeikkila on 2010-09-09
I don't actually know if it's possible.
Maybe opening the script and changing all "/lib" to "/lib64" and so on?

---

### Post by seventhsamurai on 2010-09-09
I've had this installed before on a 64 bit system. A friend did it. Should have noted down whatever it was he did.

---

### Post by 101011010010 on 2010-09-09
Hello again.
Found this old post (you might have already found it). Same driver but different model.They seemed to get it working.

[http://ubuntuforums.org/archive/index.php/t-1021755.html](http://ubuntuforums.org/archive/index.php/t-1021755.html)

---

### Post by seventhsamurai on 2010-09-09
> **101011010010 said:**
> Hello again.
Found this old post (you might have already found it). Same driver but different model.They seemed to get it working.

[http://ubuntuforums.org/archive/index.php/t-1021755.html](http://ubuntuforums.org/archive/index.php/t-1021755.html)

I did try the above. The last option given in that thread seems like it could work. Except that the installer deletes the deb file by the time the "Installation Failed" window pops up. I can even see the command there that says,

Execute: rm lexmark-inkjet-08-driver-1.0-1.i386.deb

Is there anyway for me to tweak the file such that it disables that command? That way I should be able to locate the deb file in the temp folder, force architecture and install it.

---

### Post by bredman on 2010-09-09
I downloaded this from the Lexmark website and it is a simple script. Therefore the correct method to run it is
./lexmark-inkjet-08-driver-1.0-1.i386.deb.sh

You say you tried it and it failed. How do you know it failed, and what error message did you get?

---

### Post by seventhsamurai on 2010-09-09
> **bredman said:**
> I downloaded this from the Lexmark website and it is a simple script. Therefore the correct method to run it is
./lexmark-inkjet-08-driver-1.0-1.i386.deb.sh

You say you tried it and it failed. How do you know it failed, and what error message did you get?

It says "failed to install".

Attached below is a screenshot

---

### Post by JohnHeikkila on 2010-09-09
You can see a "package architecture (i386) does not match system (amd64) which takes us back to start

---

### Post by seventhsamurai on 2010-09-09
OK!

So fueled by the links posted here, I found a way to successfully install the driver.

_**The first thing to do is from nathan726's post in this thread: [http://ubuntuforums.org/showthread.php?p=7713382](http://ubuntuforums.org/showthread.php?p=7713382)**_

```
./lexmark-inkjet-08-driver-1.0-1.i386.deb.sh --noexec --target lexmark_install
```_**Next, follow his next set of instructions:**_

Now we have extracted the files and you need to fix "is_cups_version_ok"  function near the end of the 'lexmark_install/config/run.lua' file.  It's quite easy - just open it in a text editor and insert '[COLOR=Red]--[['[/COLOR] and  '[COLOR=Red]--]][/COLOR]' like this:

```
function is_cups_version_ok()
    local bRet = true
    [COLOR=Red]--[[[/COLOR]local packager = get_system_packaging()
    local tmp_path = g_mysecurepath
    local busehome = false
    
    if tmp_path ~= nil and os.fileexists(tmp_path) then
         use home        
        if os.fileexists(tmp_path .. '/cups_packages_072006') then
            os.remove(tmp_path .. '/cups_packages_072006')
        end        
        
        if os.fileexists(tmp_path .. '/cups_packages_072006') then        
            tmp_path = install.gettempdir()
        else
            busehome = true
        end        
    else
        tmp_path = install.gettempdir()
    end

    if packager == "rpm" then
        os.execute('rpm -qa|grep cups > ' .. tmp_path .. '/cups_packages_072006')
        cups_packages = shell_execute('cat ' .. tmp_path .. '/cups_packages_072006')
        if cups_packages ~= nil and #cups_packages > 0 then
            for _,cupspackage in pairs(cups_packages) do
                cups_item = hyphen_replace(cupspackage)
                if string.find(cups_item,'cups_1.1.')==1 then
                    bRet = false
                    break
                end
            end
        else
            bRet = false 
        end
    elseif packager == "dpkg" then
        os.execute("dpkg -l | grep cups | awk '{print $2$3}' > " .. tmp_path .. "/cups_packages_072006")
        cups_packages = shell_execute('cat ' .. tmp_path .. '/cups_packages_072006')
        if cups_packages ~= nil and #cups_packages > 0 then
            for _,cupspackage in pairs(cups_packages) do
                cups_item = cupspackage
                if string.find(cups_item,'cups1.1.')==1 or string.find(cups_item,'cupsys1.1.')==1 then
                    bRet = false
                    break
                end
            end
        else
            bRet = false 
        end
    else

    end
    
    if busehome == true then
         os.remove(tmp_path .. '/cups_packages_072006')
    end
    [COLOR=Red]--]][/COLOR]
    return bRet
end
```Now the file is fixed, it's time to install it:

```
cd '/home/nathan/downloads/lexmark_install'
sudo ./startupinstaller.sh
```**The installation will definitely fail. That's OK!**
**We now jump down to Magic_Spehar's instructions in the same thread:**

 Now go to your directory lexmark_install
* In that directory you'll find a file named arch.tar   Unzip that file.
* Once unzipped you'll find lexmark-inkjet-08-driver-1.0-1.i386.deb
* Ok, now download and install the program getlibs from [http://frozenfox.freehostia.com/cappy/](http://frozenfox.freehostia.com/cappy/)  (just get getlibs-all.deb and install)  Getlibs is a wonderful tool  that takes care of all the missing 32 bit libs automatically.
* enter in a terminal:```
 sudo getlibs -i lexmark-inkjet-08-driver-1.0-1.i386.deb
```[B]
Once you have done the above, open a terminal as super user, get into the directory where the deb file is contained and type in:[/B]

```
sudo dpkg -i --force-architecture ./lexmark-inkjet-08-driver-1.0-1.i386.deb
```[B]It will install the driver.

Next, simply plug in the printer, go to System >> Administration >> Printing
Click on ADD, and you should see the printer listed.[/B]


Next adventure, trying to get the damn scanner in this thing to work!

---

### Post by bredman on 2010-09-09
I had a look at the Lexmark download site, and I searched for "lexmark-inkjet-08-driver".

There is no mention of x64 anywhere, only i386.

---

### Post by seventhsamurai on 2010-09-10
Nobody has a clue how to get the scanner in this Lexmark X2630 working? All the stuff I'm reading online is very discouraging. It seems to be a flat out NO, Lexmark scanners are unsupported.

Hoping against hope that some genius here has figured out how to get it to work.

---

### Post by seventhsamurai on 2010-09-10
Nobody has a clue how to get the scanner in this Lexmark X2630 working?  All the stuff I'm reading online is very discouraging. It seems to be a  flat out NO, Lexmark scanners are unsupported.

Hoping against hope that some genius here has figured out how to get it to work.

---

