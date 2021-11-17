# Funky metronome

Let's write a funky metronome that can handle frequent time signature shifts.

## Why?

I play the guitar and I have these small instrument bits I make up to practice. The time signatures tend to shift often, and I've never found a metronome that could handle the changes. It would be awesome to have a tiny web app that could play a click track based on a simple `json` file. Ideally, it would also show the track and where you're at.

Here's a sample recording https://drive.google.com/file/d/13F1u31xVpJu_7xf_TPFuckwsiji9gzyN/view?usp=sharing. Its rhytmic representation might look something like this:

```json
{
  "track": {
    "name": "Breeze",
    "groups": [
      [ "verse", 2],
      [ "chorus", 3]
    ],
    "tempo": 180
  },
  "groups": {
    "verse": [
        [ "eight", 2 ],
        [ "three", 1 ],
        [ "four", 1 ],
        [ "eight", 1 ]
      ],
    "chorus": [
        [ "threeDouble", 1 ],
        [ "five", 1 ],
        [ "threeDouble", 2 ]
      ]
  },
  "measures": {
    "three": "HLL",
    "threeDouble": "HLLHLL",
    "four": "HLLL",
    "five": "HLLLL",
    "eight": "HLLHLLLL"
  }
}
```

## Tasks

Backend:

 - To make things simple, the tunes could be fetched e.g. from a github repo.
 - Make an endpoint to serve the names and links of all the available tunes.
 - Make an endpoint to serve the `json` representation of an individual tune based on its `id`, `fileName`, or something of that sort.

Frontend:

 - Fetch available tunes from the API, present them. (A simple `<select>` would be more than plenty.)
 - Parse the `json` of the selected tune into some reasonable represntation that enables both playing and visualisation of the tune.
 - Present the tune to a user in a way that's easy to navigate (individual groups & their repetitions, distinct `heavy` and `light` beats).
 - Make it playable and pausable with an idicator of the current position.
 - Make it possible to edit the tempo.
