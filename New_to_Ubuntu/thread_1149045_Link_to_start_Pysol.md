---
title: "Link to start Pysol?"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by zoey_s on 2009-05-04
I am running Jaunty Jackalope.
  I installed a version of Pysol that I like better than the one in the repositories.  The only way that I can start it is to run python pysol.py in the source directory.  I tried putting  /home/user/Documents/Computer/Downloads/PysolFC1.1 python pysol.py in properties command, but that didn't work.  I'm sure that there is a way to create a link or a command, but I haven't a clue how to do that.
  I hope that someone can give me directions!
                         Thanks, zoey

---

### Post by Headbanger2510 on 2009-05-04
actually i think it should be like this:
python /home/user/Documents/Computer/Downloads/PysolFC1.1/pysol.py

---

### Post by zoey_s on 2009-05-04
> **Headbanger2510 said:**
> actually i think it should be like this:
python /home/user/Documents/Computer/Downloads/PysolFC1.1/pysol.py

Thanks, I tried that, but it didn't work.  I googled and found this;
make an alias in ~/.bashrc

pysol='python /usr/share/games/pysol/pysol.py'
 I am wondering if I should try that, but maybe it should point to my home file instead of /usr/share.

Thanks again, zoey

---

### Post by michy99 on 2009-05-04
You should point to wherever pysol.py is located.

---

### Post by zoey_s on 2009-05-04
> **michy99 said:**
> You should point to wherever pysol.py is located.

I edited  ~/.bashrc pointing it to psol.py, but that didn't work either.

zoey

---

### Post by zoey_s on 2009-05-05
This is the error message that I get when I start pysol using the command line;

/home/margo/Documents/Computer/Downloads/pysol/pysollib/init.py:156: DeprecationWarning: os.popen3 is deprecated.  Use the subprocess module.
  pin, pout, perr = os.popen3(settings.FCS_COMMAND+' --help')

thanks, zoey

---

### Post by Skrynesaver on 2009-05-05
You may be using an older version of Pysol which is making obsolete calls to the interpreter. You could install an older Pysol and run it in parallel, or possibly you just need to add the cardbacks, sounds etc... to the current version you are using.  

In Synaptic (System>Administrsation>Synaptic Package Manager) you can search for pysol, as well as the game itself there are a number of support packages with cardbacks, sounds etc.. install these and see if they provide the functionality you are missing in the default package.

Hope this helps

---

### Post by zoey_s on 2009-05-05
> **Skrynesaver said:**
> You may be using an older version of Pysol which is making obsolete calls to the interpreter. You could install an older Pysol and run it in parallel, or possibly you just need to add the cardbacks, sounds etc... to the current version you are using.  

In Synaptic (System>Administrsation>Synaptic Package Manager) you can search for pysol, as well as the game itself there are a number of support packages with cardbacks, sounds etc.. install these and see if they provide the functionality you are missing in the default package.

Hope this helps

Thank you for your suggestion.  I already had sound with my version of pysol.  I added the card sets and even installed ubuntu's version of pysol, but that didn't change anything.  My version still runs command line only and with errors.  I'm not sure about "run it in parallel".  How do I do that?

Thanks, zoey

---

### Post by Skrynesaver on 2009-05-06
What is missing from Ubuntu's Pysol, (Maintaining two versions of python to keep a second version of Pysol going is quite awkward, involves maintaining the software yourself as it isn't in the repositories)

---

