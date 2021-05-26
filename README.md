# Instructions

For questions get in contact with: thomas.mettler@lhep.unibe.ch

Here scripts are presented for the numu CC analysis using Run3 data of MicroBooNE using the analysis presented in MicroBooNE public note 1069 done by Thomas Mettler.

Please adapt the paths (usually) given in the beginning of all scripts to your local ones. Also in the library scripts!
The scripts presented here were tested and are supposed to run when given the following input files:

filename_overlay = 'NuCCana_overlay_V26_mar18.root'
filename_data = 'NuCCana_data_fullRun3.root'
filename_ext = 'NuCCana_ext_V25_G1.root'
filename_dirt = 'NuCCana_dirt_V26_weight.root'

filename_overlay = filename_overlay+'out4_noflux.root'
filename_data = filename_data+'out4.root'
filename_ext = filename_ext+'out4.root'
filename_dirt = filename_dirt+'out4.root'

All the histograms are already calculated and prepeared in My_measurement:

CV histograms + systematics (not flux) in FF_detsys.root
Total neutrino flux variations: FF_neutrino_flux.root (from a file by Zarko)
Smearing matrices and backgrounds for flux: FF_flux.root
Predictions by different generators: FF_generators.root

The most important stuff is in My_measurements and in result. Hopefully you do not need to touch the other parts...

###The recommended procedure is to (pre)calculate the uncertainties using e.g 'example.py' which gives all the fractional covariances as an output and store them in a folder per each generator.
###Then, use the Event_Rate_Model in results/ as the ploting script which gives all the needed histograms for the 2D result.
###To run these 2 scripts, no data input is needed but the precalculated histograms in My_Measurment/.
###So therefore, it is best to start running e.g example.py and then use the others only if needed...

The structure is given as follows:

## event rates:
This script plots all the event rate plots for different variables for all cuts.
cut 07: all cuts, full selection
cut 01: only 'preselection'

## My_measurement
Please check the readme file there.
Script using precalculated event rates for 2D result comparison tu different generators

## xsec
Calculates the cross section as single differential (cos(theta) and momentum) or as double differential

## result

### Event_Rate_Model
Calculates all 2D result relevant historgrams. Check if it needs precalculated covariances for the uncertainty.

### PrePareFF_totxsec
Calculates all the uncertainty and prints out the contributions regarding the total event rate or cross-section normalized.

## prepare_data
This script would collect all the histograms from all the uncertainty calculations. Not need to run this since the total distributions will be provided!
The recalculation of detctor and the other uncertainties is quite computational intensive and not forseen here...
