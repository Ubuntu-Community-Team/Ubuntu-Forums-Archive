---
title: "rhodes installation"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by asmitdutta on 2011-02-21
i am currently working on a mobile development platform called rhodes
here are some steps to install it
ok firstly ....you guys must be having ubuntu 10.04 and above
installed ....

type the following commands
$sudo apt-get install openjdk-6-jdk;
$sudo apt-get install ruby;
$sudo apt-get install rails;
$sudo apt-get install rubygems1.8;
$sudo gem install rails -V;
$sudo gem install templater -V;
$sudo gem install rhodes -V;

after these just locate where rhodes-2.*.*  is there ......
it will be in /var/lib/gems/1.8/gems/

now type this command....
$export PATH=$PATH:"/var/lib/gems/1.8/
gems/rhodes-2.2.6/bin"

download android sdk and ndk from here:

SDK:   [http://developer.android.com/sdk/index.html](http://developer.android.com/sdk/index.html)
NDK:   [http://developer.android.com/sdk/ndk/index.html](http://developer.android.com/sdk/ndk/index.html)

now extract both in your home folder and type (basically go to tools
folder)....
 $cd android-sdk-linux_86
$cd tools
$./android      (execute the emulator see if there are any
errors.....)

now type this command:
$rhodes-setup

(on typing this you will have to give the jdk,android sdk and ndk
path only)

 $ JDK path: /usr/lib/jvm/java-6-openjdk/

 $ Android SDK path: /home/[pc-name]/<android_sdk_r07-linux_x86>/

<android_sdk_r07-linux_x86>  is the android-sdk folder name

 $ Android NDK path: /home/[pc-name]/<android_ndk_r5>/

<android_ndk_r5>  is the android ndk folder name

   * the remainder of the questions related to Windows and
Blackberry: (left blank)


now type :

$rhogen app store

(here store is your application name)

now type:

$cd store

and now type:

$rake -T

(gives a list of commands)

type:

$rake run:android

now grab a cup of coffee and wait for three minutes  :D

any problems with installation you can post here....

---

### Post by asmitdutta on 2011-02-21
for more information visit my blog :

[http://asmitdutta.blogspot.com/](http://asmitdutta.blogspot.com/)

---

### Post by asmitdutta on 2011-02-21
there are more commands for creating views,models,controller
go store folder
$cd store

$rhogen model <app_name> <views>

<app_name>:store in our case

<views>:name,age,regnum,sex

this will create a folder called store...<app_name>in /home/[pcnam]/store/app/

---

### Post by lykeion on 2011-02-21
Thanks for your info asmitdutta. I checked out the GoogleTech Talks video on the [Rhodes homepage]("http://rhomobile.com/products/rhodes/"), and the project looks really interesting, kinda like [Appcelerator]("http://www.appcelerator.com/") but using Ruby on Rails. Plus the hosted build service [Rhohub]("http://rhohub.com/") looks cool too.

---

### Post by maxg70 on 2011-03-15
Hello,

I followed your instructions but when I type:
$rhogen app store
 
I get the following error:
Generating with app generator:
/usr/lib/ruby/1.8/fileutils.rb:243:in `mkdir': Permission denied - /var/lib/gems/1.8/gems/store (Errno::EACCES)
    from /usr/lib/ruby/1.8/fileutils.rb:243:in `fu_mkdir'
    from /usr/lib/ruby/1.8/fileutils.rb:217:in `mkdir_p'
    from /usr/lib/ruby/1.8/fileutils.rb:215:in `reverse_each'
    from /usr/lib/ruby/1.8/fileutils.rb:215:in `mkdir_p'
    from /usr/lib/ruby/1.8/fileutils.rb:201:in `each'
    from /usr/lib/ruby/1.8/fileutils.rb:201:in `mkdir_p'
    from /var/lib/gems/1.8/gems/templater-1.0.0/lib/templater/actions/file.rb:48:in `invoke!'
    from /var/lib/gems/1.8/gems/templater-1.0.0/lib/templater/cli/generator.rb:102:in `step_through_templates'
    from /var/lib/gems/1.8/gems/templater-1.0.0/lib/templater/cli/generator.rb:84:in `each'
    from /var/lib/gems/1.8/gems/templater-1.0.0/lib/templater/cli/generator.rb:84:in `step_through_templates'
    from /var/lib/gems/1.8/gems/templater-1.0.0/lib/templater/cli/generator.rb:75:in `run'
    from /var/lib/gems/1.8/gems/templater-1.0.0/lib/templater/cli/manifold.rb:24:in `run'
    from /var/lib/gems/1.8/gems/templater-1.0.0/lib/templater/manifold.rb:80:in `run_cli'
    from /var/lib/gems/1.8/gems/rhodes-2.3.2/bin/rhogen:33

can you help me ???    :confused::confused::confused:

thanks asmitdutta

---

### Post by maxg70 on 2011-03-16
ok 
I solved it by giving permissions to the directory

thanks

---

### Post by nilesh.chavan on 2011-03-22
[SIZE=2]hi ,[/SIZE]
[SIZE=2][/SIZE] 
[FONT=Helvetica][SIZE=2]Currently my mac machine having following setup installed :[/SIZE][/FONT]
[FONT=Helvetica][SIZE=2]i.e. Ruby 1.8.7, Ruby gem 1.6.2 and GNU make 3.81[/SIZE][/FONT]
[FONT=Helvetica][SIZE=2] [/SIZE][/FONT][FONT=Helvetica]
[FONT=Helvetica][SIZE=2]i.e. $ gem install rhodes[/SIZE][/FONT]
[FONT=Helvetica][SIZE=2]ERROR:  Could not find a valid gem 'rhodes' (>= 0) in any repository[/SIZE][/FONT]
[FONT=Helvetica][SIZE=2]ERROR:  While executing gem ... (Gem::RemoteFetcher::FetchError)[/SIZE][/FONT]
[FONT=Helvetica][SIZE=2]Errno::ETIMEDOUT: Operation timed out - connect(2) ([http://rubygems.org/latest_specs.4.8.gz](http://rubygems.org/latest_specs.4.8.gz))[/SIZE][/FONT]
[FONT=Helvetica][SIZE=2] [/SIZE][/FONT]
[FONT=Helvetica][SIZE=2]and also give error to execute rake command: [/SIZE][/FONT]
[FONT=Helvetica][SIZE=2]i.e $ rake switch_app [/SIZE][/FONT]
[FONT=Helvetica][SIZE=2]rake aborted! [/SIZE][/FONT]
[FONT=Helvetica][SIZE=2]No Rakefile found (looking for: rakefile, Rakefile, rakefile.rb, Rakefile.rb) [/SIZE][/FONT]
[FONT=Helvetica][SIZE=2]/Users/admin/.gem/ruby/1.8/gems/rake-0.8.7/lib/rake.rb:2377:in `raw_load_rakefile' [/SIZE][/FONT]
[FONT=Helvetica][SIZE=2] [/SIZE][/FONT]
[FONT=Helvetica][SIZE=2]Please provide solution for the above issue.  and if possible then please give the list of steps which need to be done to deploy rhodes application on MAC snow leopard for iPhone.[/SIZE][/FONT]
[/FONT]

---

### Post by asmitdutta on 2011-03-23
try updating or something....the rubygems version i have is 1.8.....lately i think 1.9.1 version was released....

also u could try 
$gem install rhodes --pre

---

### Post by nilesh.chavan on 2011-05-19
We have install rhostudio for eclipse and it was working properly on rhodes 2.3 version.  
After installing rhodes3.0 eclipse start giving problem while  creating the model. following error encounter whenever we try to create  model in the project .
  C:/RhoSync/ruby/lib/ruby/site_ruby/1.8/rubygems.rb:779:in  `report_activate_error': Could not find RubyGem rhodes (>= 0)  (Gem::LoadError) 
 from C:/RhoSync/ruby/lib/ruby/site_ruby/1.8/rubygems.rb:214:in `activate' 
 from C:/RhoSync/ruby/lib/ruby/site_ruby/1.8/rubygems.rb:1082:in `gem' 
 from C:/InstantRhodes/ruby/bin/rhodes:18


Please help me to solve this issue.


To see the rhodes list 

nch@OTINWISRCHP176 ~ 
$ gem list rhodes
  *** LOCAL GEMS ***
  nch@OTINWISRCHP176 ~ 
$ gem -v 
1.7.2
  nch@OTINWISRCHP176 ~ 
$ ruby -v 
ruby 1.8.7 (2010-01-10 patchlevel 249) [i386-mingw32]

---

### Post by afrodeity on 2011-09-11
> **maxg70 said:**
> ok 
I solved it by giving permissions to the directory

thanks

what permissions did you give the directory?

```

sudo chmod 777 .

```
works for me

---

### Post by nilesh.chavan on 2011-09-12
Issue was solved after installation of Rhodes 3.0 setup. before installing 3.0 i have uninstalled everything and then install Rhodes 3.0 setup.

---

