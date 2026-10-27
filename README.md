# T.E.D.D. Tasks for BO2 Zombies

Black Ops 7's T.E.D.D. Tasks in Black Ops II Zombies on Plutonium: the machine, the tasks, the reward tiers, the widget and T.E.D.D.'s own voice. A few rounds in, the machine nearest you powers on; pay 500, beat a timed task for a Rare, Epic or Legendary reward, and collect it at the machine.

## Play it

1. **[Download TEDD-Tasks.zip](https://github.com/smellofindustry/T6-TEDD-Tasks/releases/latest/download/TEDD-Tasks.zip)** and unzip it.
2. Run **Setup T.E.D.D. Tasks.bat**.
3. Start BO2 Zombies with Plutonium. Click **Mods**, pick **T.E.D.D. Tasks** and start any map.

That's it. The options are under **Settings > T.E.D.D. TASKS**. To remove it, run **Remove T.E.D.D. Tasks.bat** from the same folder.

Some of T.E.D.D.'s lines swear; they play regardless of the Graphic Content setting. Found a bug? [Open an issue](https://github.com/smellofindustry/T6-TEDD-Tasks/issues) and say which map.

## How it plays

The sequence and its timings are copied from Black Ops 7, measured in recordings of it (see `docs/SOUNDS.md`).

1. T.E.D.D. machines stand in every area of the map from the start, powered off (dark screen, eyes dark, head hanging). One per area: on Classic TranZit that's the Depot, Diner, Farm, Town and Power; Survival maps get their own area's machine.
   - Spots are hand-placed per map (TranZit, Town, Farm, Buried, Nuketown, Origins); other maps use player respawn points, then open ground near the first player.
2. From round 3-5, the machine nearest a player powers on: a lightning strike and the hellhound spawn sound, a purple Mystery Box beam, the screen lights up. 3 s later the top-center banner "A T.E.D.D. TASK HAS APPEARED" (with the place, where the spot has a name), 3 s after that T.E.D.D.'s line; his eyes light up as he speaks, his head comes up and glances toward the nearest player. He plays an advert from the machine every 30-50 s until someone buys.
3. Press use at the machine to pay 500 and start the next task from the deck. "T.E.D.D. TASK INITIATED" pops up with the task's name, his start line plays, and task music starts. 5 s later the task widget fades in and the timer starts.
   - Timers are per task, as in BO7: Melee Kill 1:30, Kill Fest 1:00, everything else 2:00. The timer shows tenths for the last 30 s and turns red for the last 10. When the time is up (or Legendary is reached) the widget holds for 2.5 s before the task ends.
   - While a kill task runs, the round's own spawns are held and purple-eyed filler zombies keep coming (10 points each, no drops); all of them die when the task ends. Their eyeballs are purple too, not just the glow: a model of both eyeballs sits on the head, and comes off with it.
   - The widget copies BO7's: badge, "T.E.D.D. TASKS" header, the objective, "TIME REMAINING", and a "MASTERY PROGRESS" bar that refills once per tier. The reward icon next to the timer appears at Rare in the rarity color (Rare blue, Epic purple, Legendary orange).
4. Each goal reached raises the reward tier with a sting, a "NEW REWARD TIER!" tag and a T.E.D.D. line. Reaching Legendary ends the task early.
5. When the timer runs out at Rare or Epic, or at Legendary right away, the widget switches to "COLLECT YOUR REWARD AT THE STATION" with the tier, a blue hex waypoint marks the machine, and the machine stays lit with "Hold [use] to Collect Your Legendary Reward" on its prompt, worded like the game's own. Each player presses use there to collect their own, as at a perk machine. The window closes when everyone has, 90 s after the first player did if someone is still to come, or when the next task's round comes.
6. If the timer runs out at no tier, the task fails: "- Cooldown and Cost Restored", as in BO7. The buyer gets the 500 back and the machine comes back on 12 s later for another go.
7. Once the reward is collected the machine powers off, and the next task comes 4-5 rounds later. **Settings > T.E.D.D. TASKS > Always Available** turns that wait into a 30 s cooldown, for practice or for players who want more tasks.

Don't want to wait at all? `set tedd_debug 1` at any time, even mid-match.

Every player collects their own reward at the machine; the rarity is the task's, the content is rolled per player. The round decides how good the item can be, and the task's difficulty only sways the odds a little (full odds in `docs/REWARDS.md`):

| Tier | Points each (easy / medium / hard) | The item, rolled per player |
|---|---|---|
| Rare | 400 / 500 / 600 | an equipment restock, bonus points, or a mystery perk (a little likelier on harder tasks) |
| Epic | 650 / 800 / 1000 | mostly a mystery perk, or an equipment restock; a Pack-a-Punch of the weapon in hand grows from a few percent at round 1 to a quarter of rolls by round 15; two mystery perks now and then |
| Legendary | 900 / 1100 / 1400 | a mystery perk, two of them, or a Pack-a-Punch (rare early, a third of rolls by round 15); a wonder weapon from round 8 on, 15% by round 20 |

A mystery perk is drunk from the bottle like at a perk machine, with no jingle and nothing saying which perk it was.

Tasks: headshots, melee, crouched kills, standing-still kills, hip-fire kills, close-range kills, explosive kills (grenades refill every 15 s), kills from higher ground, kills from lower ground, kills near the station, Kill Fest (any kills, 1:00), stay near the station, avoid damage. Kill goals grow by 50% per extra player. Tasks come as a deck: every task once, in a random order, before any repeats within a match; a new deck is shuffled once all have been done.

T.E.D.D.'s voice is BO7's own, on every map:

| Moment | Lines |
|---|---|
| Task appears | "Play your part as a cog in the capitalist machine...", "Participant engagement makes our Leadership Team smile..." |
| Waiting | adverts from the machine |
| Task starts | "R&D originally used monkeys for this..." and two more; the stay-near-the-station task has two lines of its own |
| Partway through a task | "Corporate are always watching... They say you should smile more!" |
| Reward tier goes up | "Look at you! This got you a reward..." |
| Legendary | "You've proven your worth to corporate!..." and three more |
| Timer runs out at Rare or Epic | reward line |
| Reward collected | "Congratulations! You lived!..." |
| Task failed | six fail lines |

Grief and Turned are skipped.

## Dvars

Set these in the console before starting a match, or with `+set` on the command line.

| Dvar | Default | |
|---|---|---|
| `tedd_enable` | 1 | `0` turns the mod off (e.g. alongside a mod it clashes with) |
| `tedd_cost` | 500 | Points to start a task |
| `tedd_first_round` | random 3-5 | Round the first task becomes available |
| `tedd_round_interval` | random 4-5 | Rounds between a finished task and the next one |
| `tedd_duration` | 120 | Task length in seconds for tasks without their own (Melee Kill 90, Kill Fest 60). Setting it makes every task use it |
| `tedd_start_delay` | 5 | Seconds after buying before the widget shows and the task starts counting |
| `tedd_end_hold` | 2.5 | Seconds the widget holds at 0.0 (or at the Legendary fill) before the end sequence |
| `tedd_always` | 0 | `1`: the machine is available all the time, with only a short cooldown after a reward is collected or a task fails. Can be set mid-match. This is the Always Available switch in Settings > T.E.D.D. TASKS |
| `tedd_cooldown` | 30 | Seconds of that cooldown |
| `tedd_debug` | 0 | 1 = station right away, next to you, and god mode; 2 = the task also starts itself. Can be set mid-match. |
| `tedd_force_task` | | Always pick this task id (e.g. `headshot`) |
| `tedd_goal_scale` | 1 | Multiplies every goal (0.2 for quick tests) |
| `tedd_force_item` | | Test knob: every reward roll is this item (`perk`, `perk2`, `pap`, `equipment`, `wonder`, `points`) |
| `tedd_reward_round` | | Test knob: rewards roll as if it were this round |
| `tedd_debug_weapon` | | With debug on, the host starts with this weapon in hand (e.g. `ak74u_zm`, to check a Pack-a-Punch reward on it) |
| `tedd_mark` | | With debug on, `set tedd_mark 1` writes your position to console.log as a station spot |
| `tedd_debug_beam` | 0 | `+set` before the map loads: the stock Mystery Box light and T.E.D.D.'s purple copy side by side (spawning off) |

Console commands (host, no debug needed; each runs once and clears itself):

| Command | |
|---|---|
| `set tedd_spawn 1` | Power T.E.D.D. on with a task available right now (random task) |
| `set tedd_spawn <task id>` | Same, with that task, e.g. `set tedd_spawn headshot` |
| `set tedd_fail 1` | End the running task as failed (no reward, cost refunded, machine back on in 12 s) |
| `set tedd_collect 1` | Collect the host's waiting reward without walking to the machine |
| `set tedd_progress <n>` | Add n progress to the running task (kills, or seconds for timed tasks); repeat to climb the tiers |
| `set tedd_autoprogress <n>` | Progress climbs by itself, n per second, through Rare, Epic and Legendary. Stays on for later tasks; `set tedd_autoprogress 0` turns it off |

Task ids: `headshot`, `melee`, `crouch`, `still`, `hipfire`, `close`, `explosive`, `higher`,
`lower`, `near`, `killfest`, `stay`, `nodamage`.

## Custom maps and other mods

The mod is written to degrade rather than break on maps and mods it doesn't know:

- No hand-picked spots for the map: T.E.D.D. goes on one of the mode's player respawn points, then
  the map's initial spawn points, then open ground in front of the first player.
- No zone manager: every spot counts as open.
- No stock round counters (custom round logic): kill tasks run without the purple fillers.
- Zombie models without the stock eye bone keep their own eyes; a head the eyeball table doesn't know wears its map's first eyeball model.
- Missing power-ups, perks or Ray Guns: those rewards are skipped.
- No "intro done" flag: the mod starts after 30 seconds anyway.
- Grief and Turned are skipped on purpose; `tedd_enable 0` turns it off anywhere.

[License](LICENSE.md) (CC BY-NC-SA 4.0) · Not affiliated with Activision, Treyarch or Plutonium.
