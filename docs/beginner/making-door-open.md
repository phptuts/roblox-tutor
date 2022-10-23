# Making a door open

We'll making a door open and close in Roblox.

## Objectives

- Variables
- While Loops
- For Loops
- Parts
- wait function
- functions
- Position and Vector3
- Touch Events
- Playing Sound

## Project

[Project File](https://www.roblox.com/library/11362863303/Open-Door-House-Beginner-Lesson)

## Code Version 1

```lua
local doorPart = script.Parent.Door

while true do
	for i = 0, 9 do
		doorPart.Position = doorPart.Position + Vector3.new(0,0, 1)
		wait(.5)
	end
	
	for i = 0, 9 do
		doorPart.Position = doorPart.Position + Vector3.new(0,0, -1)
		wait(.5)
	end
end
```
## Final Version

```lua
local doorPart = script.Parent.Door
local openPart = script.Parent.Open
local boomSound = script.Parent.Boom
local doorMoving = false

function moveDoor() 
	-- loop 10 times through the loop 
	for i = 1, 10 do
		-- move the door one stud in the z direction
		doorPart.Position = doorPart.Position + Vector3.new(0,0, 1)
		wait(.5)
	end
	-- wait 2 seconds
	wait(2)
	-- do it in reverse
	for i = 1, 10 do
		doorPart.Position = doorPart.Position + Vector3.new(0,0, -1)
		wait(.5)
	end
end

function onTouch(part) 
	-- Is thing touching this a player
	local hum = part.parent:FindFirstChild("Humanoid")
	-- if is it a human the door is not moving open the door
	if hum and doorMoving == false then
		doorMoving = true
		boomSound:Play()
		moveDoor()
		wait(2)
		doorMoving = false
	end
end

openPart.Touched:Connect(onTouch)
```

## Challenges

1\. Create a part inside the building that when you touch it opens the door.

2\. Create a part inside the building that when you click it opens the door.

3\. Create a part inside the building that you touch it makes the baseplate and the floor transparent and not collidable.
