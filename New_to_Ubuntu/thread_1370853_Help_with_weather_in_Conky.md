---
title: "Help with weather in Conky"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by Peppermynthe on 2010-01-02
Hello,

If anyone has installed/setup Conky using the following site 

[http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/](http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/)

I could use some help with the weather. I have set it up the way I want. However I can not get the weather to show. I have looked through the comments and have made a few changes to no avail. All that is currently showing is "F/F" and a big space. 

Changed the website to...

```
w3m -dump http://weather.yahoo.com/San-Francisco-California-United-States/USCA0987/forecast.html | grep -A21 "Current" | sed 's/DEG/°/g' > $plik 
```

And changed some of the settings,

```
# ustalenie wartoÂ¶ci zmiennych

	stan=`head -n2 $plik | tail -n1` # Conditions

	temp=`tail -n2 $plik | awk '{print $1}'` # Temperature

	tempo=`head -n7 $plik | tail -n1` # Barometer

	cisn=`head -n9 $plik | tail -n1` # Humidity

	wiatr=`head -n15 $plik | tail -n1` # Wind

	wilg=`head -n11 $plik | tail -n1` # Visibility

	wsch=`head -n17 $plik | tail -n1` # Sunrise

	zach=`head -n19 $plik | tail -n1` # Sunset
```


Within the pogodynka.sh file. I've used google translate from Polish to English of the whole file, and I still don't understand what I'm supposed to change or do.

Any help would be appreciated!

---

### Post by duanedesign on 2010-01-04
from what i can see the address should be

```
w3m -dump http://weather.yahoo.com/forecast/"$kod".html | grep -A21 "Current" | sed 's/DEG/°/g' > $plik
```

and you set the kod variable in pogodynka.sh  (for San Francisco)

```
kod=USCA0987
```

to create the blank file you can run.
```
touch ~/weather
```

additionally launch conky from the Terminal to see if you get any error messages that might help. Open a Terminal and issue the command.

```
conky
```

For weather in Conky I use ConkyForecast. Here are instructions for installing it.

add the repository.

```
sudo add-apt-repository ppa:m-buck/conky
```

then install

```
sudo apt-get update && sudo apt-get install conkyforecast
```

To register and obtain the necessary codes you need to visit the following url and fill out the form: [http://www.weather.com/services/xmloap.html](http://www.weather.com/services/xmloap.html)

After successfully completing the form, you will then receive a couple of
emails providing you with the necessary codes to update your .conkyForecast.config

To copy and edit the config file, using the command line , run the following two commands in a terminal, one after the other:

```
cp /usr/share/conkyforecast/conkyForecast.config ~/.conkyForecast.config && nano ~/.conkyForecast.config
```

To identify the location code for your town/city the following URL should be used, replacing NORWICH with the one you're looking up :

```
http://xoap.weather.com/search/search?where=NORWICH
```

In the /usr/share/conkyforecast/example folder you'll find 2 files, conkyrc and conkyForecast.template Take a look at these to get an idea of what is needed for this to work. You can run conky using the example file.

```
conky -c /usr/share/conkyforecast/example/conkyrc &
```

The important thing to note now is that the script is called using this in Conky:

```
{execi 1800 conkyForecast ...options...}
```


[additional info]("http://ubuntuforums.org/showthread.php?t=869328") on ConkyForecast

---

