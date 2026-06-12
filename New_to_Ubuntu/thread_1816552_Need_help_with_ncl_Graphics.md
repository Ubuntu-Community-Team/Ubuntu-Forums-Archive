---
title: "Need help with ncl Graphics"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by avi k on 2011-08-02
[SIZE=3]I try to run the model wrf with [/SIZE][SIZE=3]ncl[/SIZE][SIZE=3] Graphics , I've used this script I'm attaching for example:
 The script works, but my problem is: How do I keep the picture in My computer[/SIZE][SIZE=3] so that I can for example display it on the forum, does anyone know these scripts?.

the script:

[http://pastebin.com/706pVvhT](http://pastebin.com/706pVvhT)
[/SIZE]

---

### Post by cavh on 2011-08-02
1. What command do you run to generate the image? 
2. What is the file format of the image that is generated (e.g. JPG or PNG, etc.)?

Once we know this we should be able to put together a small Bash script which runs the command to generate the image and then saves it to your desktop.

---

### Post by avi k on 2011-08-02
1) The command I use is: ncl ncldo1.ncl (This command runs the script).

 2) As far as I could understand the script, the following lines are those that create the file format :

; We generate plots, but what kind do we prefer?
  type = "x11"
  type = "pdf"
; type = "ps"
; type = "ncgm"
  wks = gsn_open_wks(type,"plt_Precip")


How do I change it to a png or jpg format still i could not understand, I have not found an answer to this  in Google.

---

### Post by cavh on 2011-08-03
Please post all of the script so we can see what the configuration options are.

---

### Post by avi k on 2011-08-03
in My first message I put all of the script: Here's the script again:



;   Example script to produce plots for a WRF real-data run,
;   with the ARW coordinate dynamics option.

load "$NCARG_ROOT/lib/ncarg/nclscripts/csm/gsn_code.ncl"
load "$NCARG_ROOT/lib/ncarg/nclscripts/wrf/WRFUserARW.ncl"

begin
;
; The WRF ARW input file.  
; This needs to have a ".nc" appended, so just do it.
  a = addfile("./wrfout_d01_2005-08-28_00:00:00.nc","r")


; We generate plots, but what kind do we prefer?
  type = "x11"
  type = "pdf"
; type = "ps"
; type = "ncgm"
  wks = gsn_open_wks(type,"plt_Precip")


; Set some basic resources
  res = True
  res@MainTitle = "REAL-TIME WRF"

  pltres = True
  mpres = True
  mpres@mpGeophysicalLineColor = "Black"
  mpres@mpNationalLineColor    = "Black"
  mpres@mpUSStateLineColor     = "Black"
  mpres@mpGridLineColor        = "Black"
  mpres@mpLimbLineColor        = "Black"
  mpres@mpPerimLineColor       = "Black"

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

; What times and how many time steps are in the data set?
  FirstTime = True
  times  = wrf_user_list_times(a)  ; get times in the file
  ntimes = dimsizes(times)         ; number of times in the file

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

  do it = 0,ntimes-1,2             ; TIME LOOP

    print("Working on time: " + times(it) )
    if (FirstTime) then            ; Save some times for tracking tendencies
      times_sav = times(it)
    end if
    res@TimeLabel = times(it)   ; Set Valid time to use on plots

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
; First get the variables we will need        

    slp = wrf_user_getvar(a,"slp",it)  ; slp
      wrf_smooth_2d( slp, 3 )            ; smooth slp

  ; Get non-convective, convective and total precipitation
  ; Calculate tendency values                               
    rain_exp = wrf_user_getvar(a,"RAINNC",it)
    rain_con = wrf_user_getvar(a,"RAINC",it)
    rain_tot = rain_exp + rain_con
    rain_tot@description = "Total Precipitation"

    if( FirstTime ) then
      if ( it .eq. 0 ) then
        rain_exp_save = rain_exp
        rain_con_save = rain_con
        rain_tot_save = rain_tot
      else
        rain_exp_save = wrf_user_getvar(a,"RAINNC",it-1)
        rain_con_save = wrf_user_getvar(a,"RAINC",it-1)
        rain_tot_save = rain_exp_save + rain_con_save
        FirstTime = False
        times_sav = times(it-1)
      end if
    end if

    rain_exp_tend = rain_exp - rain_exp_save
    rain_con_tend = rain_con - rain_con_save
    rain_tot_tend = rain_tot - rain_tot_save
    rain_exp_tend@description = "Explicit Precipitation Tendency"
    rain_con_tend@description = "Param  Precipitation Tendency"
    rain_tot_tend@description = "Precipitation Tendency"

  ; Bookkeeping, just to allow the tendency at the next time step
    rain_exp_save = rain_exp
    rain_con_save = rain_con
    rain_tot_save = rain_tot

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

    if( .not. FirstTime ) then     ; We will skip the first time

      ; Plotting options for Sea Level Pressure
        opts_psl = res          
        opts_psl@ContourParameters = (/ 900., 1100., 2. /)
        opts_psl@cnLineColor       = "Blue"
        opts_psl@cnInfoLabelOn     = False
        opts_psl@cnLineLabelFontHeightF = 0.01
        opts_psl@cnLineLabelPerimOn = False
        opts_psl@gsnContourLineThicknessesScale = 1.5
        contour_psl = wrf_contour(a,wks,slp,opts_psl)
        delete(opts_psl)
    

      ; Plotting options for Precipitation
        opts_r = res                        
        opts_r@UnitLabel            = "mm"
        opts_r@cnLevelSelectionMode = "ExplicitLevels"
        opts_r@cnLevels             = (/ .1, .2, .4, .8, 1.6, 3.2, 6.4, \
                                        12.8, 25.6, 51.2, 102.4/)
        opts_r@cnFillColors         = (/"White","White","DarkOliveGreen1", \
                                        "DarkOliveGreen3","Chartreuse", \
                                        "Chartreuse3","Green","ForestGreen", \
                                        "Yellow","Orange","Red","Violet"/)
        opts_r@cnInfoLabelOn        = False
        opts_r@cnConstFLabelOn      = False
        opts_r@cnFillOn             = True
    

      ; Total Precipitation (color fill)
        contour_tot = wrf_contour(a,wks, rain_tot, opts_r)
    
      ; Precipitation Tendencies 
        opts_r@SubFieldTitle = "from " + times_sav + " to " + times(it)
    
        contour_tend = wrf_contour(a,wks, rain_tot_tend,opts_r) ; total (color)
        contour_res = wrf_contour(a,wks,rain_exp_tend,opts_r)   ; exp (color)
        opts_r@cnFillOn = False
        opts_r@cnLineColor = "Red4"
        contour_prm = wrf_contour(a,wks,rain_con_tend,opts_r)   ; con (red lines)
        delete(opts_r)



      ; MAKE PLOTS                                       

        ; Total Precipitation 
          plot = wrf_map_overlays(a,wks,contour_tot,pltres,mpres)

        ; Total Precipitation Tendency + SLP
          plot = wrf_map_overlays(a,wks,(/contour_tend,contour_psl/),pltres,mpres)

        ; Non-Convective and Convective Precipiation Tendencies
          plot = wrf_map_overlays(a,wks,(/contour_res,contour_prm/),pltres,mpres)

    end if    ; END IF FOR SKIPPING FIRST TIME

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

    times_sav = times(it)
    FirstTime = False
  end do        ; END OF TIME LOOP

end

---

### Post by cavh on 2011-08-04
Try this command:

```
ncl ncldo1.ncl > ~/Desktop/output.pdf
```

and check if a PDF is generated on your desktop.

If it doesn't work, run the command in the manner you've been doing it previously, and see if a PDF is generated in the directory from which you run the command.

---

### Post by avi k on 2011-08-05
Thank you.
 Before I tried the command I changed it , so it's would create a png image format.
Now I ran the script And is working,You can see in image 1, he created a map:

[http://upndown.me/xbwnpsyiwu7r/wrf1.png.html](http://upndown.me/xbwnpsyiwu7r/wrf1.png.html)

I clicked on the map, then it creates another map, as shown by image 2.

[http://upndown.me/x8htnfa1gy4y/wrf2.png.html](http://upndown.me/x8htnfa1gy4y/wrf2.png.html)

After you click on the map again, it closes, and It writes an error message in the Console:

user@user-desktop:~/WRF/WRFV3/test/em_real$ ncl ncldo1.nc > ~/Desktop/output.png 
STOP Error_in_finding_100_hPa_up
user@user-desktop:~/WRF/WRFV3/test/em_real$ 

I do not know why the error is created.
an image is Created in my desktop,But I can not open the image, he writes to me "Could not open the image".

[http://upndown.me/fmbihm4r6x8l/wrf3.png.html](http://upndown.me/fmbihm4r6x8l/wrf3.png.html)

Can you tell me what's wrong, I'm attaching the script I used this time, it's another script:

;   Example script to produce plots for a WRF real-data run,
;   with the ARW coordinate dynamics option.

load "$NCARG_ROOT/lib/ncarg/nclscripts/csm/gsn_code.ncl"
load "$NCARG_ROOT/lib/ncarg/nclscripts/wrf/WRFUserARW.ncl"

begin
;
; The WRF ARW input file.  
; This needs to have a ".nc" appended, so just do it.
  a = addfile("./wrfout_d01_2005-08-28_00:00:00.nc","r")

; We generate plots, but what kind do we prefer?
  type = "x11"
; type = "png"
  wks = gsn_open_wks(type,"plt_Surface1")

; Set some basic resources
  res = True
  res@MainTitle                   = "REAL-TIME WRF"

  pltres = True
  mpres = True


;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

; What times and how many time steps are in the data set?
  times  = wrf_user_list_times(a)  ; get times in the file
  ntimes = dimsizes(times)         ; number of times in the file

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

  do it = 0,ntimes-1,2             ; TIME LOOP

    print("Working on time: " + times(it) )
    res@TimeLabel = times(it)   ; Set Valid time to use on plots


;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
; First get the variables we will need        

    slp = wrf_user_getvar(a,"slp",it)    ; slp
      wrf_smooth_2d( slp, 3 )            ; smooth slp
    tc = wrf_user_getvar(a,"tc",it)      ; 3D tc 
    td = wrf_user_getvar(a,"td",it)      ; 3D td 
    u  = wrf_user_getvar(a,"ua",it)      ; 3D U at mass points
    v  = wrf_user_getvar(a,"va",it)      ; 3D V at mass points
    td2 =  wrf_user_getvar(a,"td2",it)   ; Td2 in C
    tc2 = wrf_user_getvar(a,"T2",it)     ; T2 in Kelvin
       tc2 = tc2-273.16                  ; T2 in C
    u10 = wrf_user_getvar(a,"U10",it)    ; u at 10 m, mass point
    v10 = wrf_user_getvar(a,"V10",it)    ; v at 10 m, mass point

    tf2 = 1.8*tc2+32.                    ; Turn temperature into Fahrenheit
      tf2@description = "Surface Temperature"
      tf2@units = "F"
    td_f = 1.8*td2+32.                   ; Turn temperature into Fahrenheit
      td_f@description = "Surface Dew Point Temp" 
      td_f@units = "F"
    u10 = u10*1.94386                    ; Turn wind into knots
    v10 = v10*1.94386
      u10@units = "kts"
      v10@units = "kts"

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

    ; Plotting options for T                
      opts = res                         
      opts@cnFillOn = True  
      opts@ContourParameters = (/ -20., 90., 5./)
      opts@gsnSpreadColorEnd = -3  ; End third from the last color in color map
      contour_tc = wrf_contour(a,wks,tf2,opts)
      delete(opts)


    ; Plotting options for Td
      opts = res         
      opts@cnFillOn = True 
      opts@cnLinesOn = True
      opts@cnLineLabelsOn = True
      opts@ContourParameters = (/ -20., 90., 5./) 
      opts@cnLineLabelBackgroundColor = -1
      opts@gsnSpreadColorEnd = -3  ; End third from the last color in color map
      contour_td = wrf_contour(a,wks,td_f,opts)
      delete(opts)


    ; Plotting options for SLP                     
      opts = res         
      opts@cnLineColor = "Blue"
      opts@cnHighLabelsOn = True
      opts@cnLowLabelsOn = True
      opts@ContourParameters = (/ 900., 1100., 4. /)
      opts@cnLineLabelBackgroundColor = -1
      opts@gsnContourLineThicknessesScale = 2.0
      contour_psl = wrf_contour(a,wks,slp,opts)
      delete(opts)

    ; Plotting options for Wind Vectors                 
      opts = res         
      opts@FieldTitle = "Wind"       ; overwrite Field Title
      opts@NumVectors = 47           ; density of wind barbs
      vector = wrf_vector(a,wks,u10,v10,opts)
      delete(opts)
  

    ; MAKE PLOTS                                       
      plot = wrf_map_overlays(a,wks,(/contour_tc,contour_psl,vector/),pltres,mpres)
      plot = wrf_map_overlays(a,wks,(/contour_td,vector/),pltres,mpres)

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

  end do        ; END OF TIME LOOP

end

---

### Post by cavh on 2011-08-08
See [http://www.ncl.ucar.edu/FAQ/#o_formats_004]("http://www.ncl.ucar.edu/FAQ/#o_formats_004").

If this answers your question, please mark this thread as SOLVED using the thread tools link at the top of the page.

---

### Post by avi k on 2011-08-09
[SIZE=3]Thanks  for your help.[/SIZE]

---

