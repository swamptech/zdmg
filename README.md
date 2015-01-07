# DOOM MIDI Setup Guide 
Revision 1.1 (Jan. 6, 2015)  
by Swampfox - [swamptech@host.sk](mailto:swamptech@host.sk)  
To /vr/ with love

---
# Softsynths
Software Synthesizers (softsynths) can be used to play back MIDI music without any external music hardware.
(G)ZDoom has a selection to choose from.

[NOTE: Although its listed under "_MIDI Devices_," _FMOD_ doesn't do MIDI synthesis by itself, it falls back on system default for that.]

## BASSMIDI
Uses Soundfonts for instruments. It can even utilize multiple sets of them containing different instruments, if desired. Under Windows (to which it is exclusive), this is possibly the best choice. It even works system-wide, so any game or program that uses MIDIs can take advantage of it. Supports reverb, chorus, and variation effects, as well. 

**Instructions:**  
* Download and install the BASSMIDI Driver (Available here: [http://www.kode54.net/bassmididrv/](http://www.kode54.net/bassmididrv) or [DDL to the latest version](http://www.kode54.net/bassmididrv/bassmididrv.exe))
* Once installed, find _BASSMIDI Driver Configuration_ in your Start Menu and launch it.
* In the _Soundfonts_ tab, click _Add_, and open your .sf2 Soundfont file using the dialog box.
* Click _Apply_.
* To use the synthesizer system-wide, go to the _Advanced_ Tab, and in the _Default MIDI Synth_ drop-down box, change it from _Microsoft GS Wavetable Synth_ to _BASSMIDI Driver (Port A)_, and click _Apply_.
* Fire up (G)ZDoom, under _Options->Sound Options_, set your _MIDI Device_ to _BASSMIDI Driver (Port A)_, and hit _Restart Sound_. Have fun with your new sound!

## Fluidsynth
Uses Soundfonts for instruments.

**Windows Instructions:**  
* Place fluidsynth.dll (Available here: [http://www.zdoom.org/files/fluidsynth.7z](http://www.zdoom.org/files/fluidsynth.7z)) in the same folder as (g)zdoom.exe.
* * Open up zdoom.ini (or zdoom-YOURUSERNAME.ini) and look for _fluid_patchset_ and have it equal the file path for the sound font you want to use so it looks similar to this:

		fluid_patchset=C:\Users\Yourusername\soundfonts\Fluid_R3.sf2

* Avoid using a path or filename with spaces in it, it may cause problems.
* Fire up (G)ZDoom, under _Options->Sound Options_, set your _MIDI Device_ to _FluidSynth_, and hit _Restart Sound_. Have fun with your new sound!

## Timidity++
Can use Soundfonts or GUS Patches for instruments.
But it can be buggy at times and is a pain to configure, so I recommend FluidSynth over it, but if you really want to use it, here:

**Windows Instructions:**  
* Create a folder inside your (g)zdoom.exe folder called timidity.
* Download a special build of Timidity++ for ZDoom (Available here: [http://www.zdoom.org/files/timidity4zdoom2.zip](http://www.zdoom.org/files/timidity4zdoom2.zip))
* Edit the _timidity.cfg_ file in a text editor like Notepad.
	* If using a Soundfont:
		* Make the first two lines: _dir "soundfont-folder-path"_ and _soundfont "filename.sf2"_, respectively, so it looks similar to this:

				dir C:\Users\Yourusername\soundfonts
				soundfont Fluid_R3.sf2

	* If using GUS Patches:
		* Make the first two lines: _dir "patches-folder-path"_ and _source "patch-config-file-name.cfg"_, respectively, so it looks similar to this:

				dir C:\Users\Yourusername\patches\8MBGMSFX
				source default.cfg

* Open up zdoom.ini (or zdoom-YOURUSERNAME.ini) and look for _timidity_exe_ and have it equal filepath of the timidity executable so it looks similar to this:

		timidity_exe=C:\Games\ZDoom\timidity\timidity.exe

	* Avoid using a path or filename with spaces in it, it may cause problems.
* Fire up (G)ZDoom, under _Options->Sound Options_, set your _MIDI Device_ to _Timidity_, and hit _Restart Sound_.  Have fun with your new sound!

## OPL Synth Emulation
"OPL" refers to a series of FM Sound Chips by Yamaha, which was popularly used in many sound cards during the early to mid 1990's, including the Creative's _Sound Blaster_ series, and many of its clones. The .MUS format and Doom's sound engine was designed to tune the music for either FM Synthesis or Wavetable Synthesis, depending on what the user had.
(G)ZDoom comes with options to change how the emulation of this sound chip works built right into the engine, so inital setup is easy, but you can fine-tune it, if you'd like.

**Instructions:**

* Fire up (G)ZDoom, under _Options->Sound Options_, set your _MIDI Device_ to _OPL Synth Emulation_, and hit _Restart Sound_. Should work and you can stop reading this section now if it sounds alright to you.
	* Under _Options->Sound Options->Advanced Options->OPL Synthesis_, you can change some stuff.
		* _Number of Emulated OPL Chips_: Can be set between 1-8. Increasing this will allow for higher polyphony (more instruments, audio channels at once.) Its rare you would find a MIDI that uses 16 or more channels simultaneously and not hurt your ears, so you really don't need very many chips.  
		Recommended: _2_
		* _Full MIDI Stereo Panning_: Provides actual stereo sound, as opposed to just the center channel coming out of two speakers.  
		Recommended: _On_.
		* _OPL Emulator Core_: Different emulators might affect the sound/quality of the music. Negligible speed difference between them. *MAME OPL2*, although very accurate to the real chip, emulates the less-capable OPL chip, the Yamaha YM3812 (OPL2), instead of the Yamaha YMF262 (OPL3). The above two options, however, may increase its capabilities.  
		Recommended: _DOSBox OPL3_

Personally, my favorite OPL3 emulator is [ADLMIDI](http://bisqwit.iki.fi/source/adlmidi.html) by [Bisqwit](http://bisqwit.iki.fi/), follwed by [Ken Silverman](http://advsys.net/ken/default.htm)'s ADLIBEMU. If you don't know who the latter person is, shame on you!  
[_He created the BUILD 3D game engine, which powered games like Duke Nukem 3D, Blood, Shadow Warrior, etc._]

---

# Soundfonts
Soundfonts are collections of audio samples and/or instruments for use with MIDI Synthesizers.
You'll generally want to find one that is at least a full GM (General MIDI) set, meaning it contains the common 128 instruments defined by the standard. But if you find one that are compatible with extensions to that standard, such as _Yamaha XG_ or _Roland GS_, its likely they contain those instruments in addition to the normal GM set.  
Most Soundfonts these days are generally of good quality/fidelity, and is often up to personal preference or constraints (large ones may take up HDD space, and RAM when too many instruments are loaded at once, but that really isn't much of a problem these days.)
There are a plethora of soundfonts out there, but here are some ones I recommend, going from smallest to largest size:

**8MBGMSFX**  
Author: E-mu Technologies / Creative Technology Ltd.  
Current Version: N/A  
File Size: 8MB  
Download: [http://www.alsa-project.org/~james/sound-fonts/8MBGMSFX.SF2](http://www.alsa-project.org/~james/sound-fonts/8MBGMSFX.SF2)

This was originally bundled with the higher-end Sound Blaster AWE, Live!, and Audigy soundcards. Released with permission. Its not mind-blowing, but its adequate. Also available as a set of GUS patches on, believe it or not, Doomworld's /idgames mirror, as [_8MBGMPAT.ZIP_](http://www.doomworld.com/idgames/?file=utils/sound_edit/8mbgmpat.zip).
 
**GeneralUser GS**  
Author: S. Christian Collins  
Current Version: 1.44  
File Size: 28MB  
Download: [http://www.schristiancollins.com/generaluser.php](http://www.schristiancollins.com/generaluser.php)

Note there is a special version tuned for _FluidSynth_. This one is impressive due to how realistic the sound can be despite its low filesize.

**¥Weeds¥ General MIDI**  
Author: Rich "Weeds" Nagel  
Current Version: 3.0 (March 1, 2010)  
File Size: 54MB  
Download: [http://www.simpilot.net/~richnagel/#soundfonts](http://www.simpilot.net/~richnagel/#soundfonts)

It's pretty good. This guy is a major DOOMer, too. He's _rfnagel_ on Doomworld.

**Arachno Soundfont** 
Author: Maxime Abbey  
Current Version: 1.00  
File Size: 80MB  
Download: [http://www.arachnosoft.com/main/soundfont.php](http://www.arachnosoft.com/main/soundfont.php)  

**Timbres of Heaven**  
Author: Don Allen  
Current Version: 2.02 (March 9, 2014)  
File Size: 250MB  
Download: [http://midkar.com/soundfonts/](http://midkar.com/soundfonts/)

---
# Glossary

**MUS lumps**  
Doom originally .MUS lumps for music, which are essentially MIDIs, but have extra information in them to tune instruments for popular soundcards at the time. MUS lumps have a maximum file size of 64 kilobytes per song.

**MIDI**  
Acronym for "Musical Instrument Digital Interface." Pronounced "mid ee."
It is the standard for electronic instruments such as keyboards, drum machines, etc., to communicate with each other.
In the context of MIDI files, often on computers, they are files that contain instructions of notes and instruments to be able to play a song.

---
# Addendum/Changelog  
**January 6, 2015 - 21:52 (PST)**
I will update this guide further in my spare time. If you have any comments, questions, or suggestions, feel free to email me.
* Added BASSMIDI instructions
* Fixed some spelling and formatting errors
* [_Project Doom_(prjdoom.zip)](http://www.doomworld.com/idgames/index.php?file=music/prjdoom.zip), was credited to ¥Weeds¥, but it was actually created by Jay Reichard. ¥Weeds¥ did the [soundtrack](http://www.simpilot.net/~richnagel/#eternal_doom_soundtrack) for TeamTNT/Eternal's popular 1997 megawad [_Eternal DOOM_](http://www.doomworld.com/idgames/index.php?file=themes/TeamTNT/eternal/eternal.zip).

**December 31, 2014 - 23:56 (PST)**
No where near close to done like I thought I would, but I still have way more shit to do.
In the next revision(s), look for:
* BASSMIDI Setup, Virtual MIDI Patch Cable
* MIDI in GNU/Linux: ALSA, PulseAudio, and a softsynth as a daemon
* Other Sourceports and their support
* Old school DOS shit and moar
