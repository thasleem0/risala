<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Text Box Example</title>
<style>
    .container {
        margin: 20px;
    }
    .textbox {
        margin-bottom: 10px;
    }
    .completed {
        color: green;
    }
    .task-container {
        border: 1px solid #ccc;
        padding: 10px;
        margin-top: 10px;
    }
</style>
</head>
<body>

<div class="container">
    <h2>Page 1</h2>
    <input type="text" id="textInput" class="textbox">
    <button onclick="showText()">Show Text on Another Page</button>
</div>

<div id="anotherPage" style="display:none;">
    <div class="container">
        <h2>Page 2</h2>
        <div id="displayText"></div>
    </div>
</div>

<script>
    window.onload = function() {
        var storedTasks = JSON.parse(localStorage.getItem('tasks'));
        if (storedTasks) {
            document.getElementById("displayText").innerHTML = storedTasks;
            document.getElementById("anotherPage").style.display = "block";
        }
    }

    function showText() {
        var text = document.getElementById("textInput").value;
        var displayText = document.createElement("div");
        if (text.toLowerCase().includes("offer letter")) {
            displayText.innerHTML = '<div class="task-container">' + 
                '<div>' + text + '</div>' +
                 '<div>' +
                    '<button onclick="deleteText(this)">Delete</button>' +
                    '<button onclick="completeTask(this)">Tick</button>' +
                '</div>' +
                '<div>' +
                    '<input type="text" placeholder="Offer letter">' +
                    '<button onclick="deleteText(this)">Delete</button>' +
                    '<button onclick="completeTask(this)">Tick</button>' +
                '</div>' +
                '<div>' +
                    '<input type="text" placeholder="Insurance">' +
                    '<button onclick="deleteText(this)">Delete</button>' +
                    '<button onclick="completeTask(this)">Tick</button>' +
                '</div>' +
                '<div>' +
                    '<input type="text" placeholder="Fees Payment">' +
                    '<button onclick="deleteText(this)">Delete</button>' +
                    '<button onclick="completeTask(this)">Tick</button>' +
                '</div>' +
                '<div>' +
                    '<input type="text" placeholder="Entry permit">' +
                    '<button onclick="deleteText(this)">Delete</button>' +
                    '<button onclick="completeTask(this)">Tick</button>' +
                '</div>' +
                '<div>' +
                    '<input type="text" placeholder="Change status">' +
                    '<button onclick="deleteText(this)">Delete</button>' +
                    '<button onclick="completeTask(this)">Tick</button>' +
                '</div>' +
                '<div>' +
                    '<input type="text" placeholder="Tawjeeh">' +
                    '<button onclick="deleteText(this)">Delete</button>' +
                    '<button onclick="completeTask(this)">Tick</button>' +
                '</div>' +
                '<div>' +
                    '<input type="text" placeholder="contract submmission">' +
                    '<button onclick="deleteText(this)">Delete</button>' +
                    '<button onclick="completeTask(this)">Tick</button>' +
                '</div>' +
                '<div>' +
                    '<input type="text" placeholder="Stamping">' +
                    '<button onclick="deleteText(this)">Delete</button>' +
                    '<button onclick="completeTask(this)">Tick</button>' +
                '</div>' +
            '</div>';
        } else if (text.toLowerCase().includes("renew") || text.toLowerCase().includes("renewal")) {
            displayText.innerHTML = '<div class="task-container">' + 
                '<div>' + text + '</div>' +
                '<div>' +
                    '<button onclick="deleteText(this)">Delete</button>' +
                    '<button onclick="completeTask(this)">Tick</button>' +
                '</div>' +
                '<div>' +
                    '<input type="text" placeholder="Renew Application">' +
                    '<button onclick="deleteText(this)">Delete</button>' +
                    '<button onclick="completeTask(this)">Tick</button>' +
                '</div>' +
                '<div>' +
                    '<input type="text" placeholder="Insurance">' +
                    '<button onclick="deleteText(this)">Delete</button>' +
                    '<button onclick="completeTask(this)">Tick</button>' +
                '</div>' +
                '<div>' +
                    '<input type="text" placeholder="Tawjeeh">' +
                    '<button onclick="deleteText(this)">Delete</button>' +
                    '<button onclick="completeTask(this)">Tick</button>' +
                '</div>' +
                '<div>' +
                    '<input type="text" placeholder="Contract Submission">' +
                    '<button onclick="deleteText(this)">Delete</button>' +
                    '<button onclick="completeTask(this)">Tick</button>' +
                '</div>' +
            '</div>';
        } else {
            displayText.innerHTML = '<div class="task-container">' + 
                '<div>' + text + '</div>' +
                '<div>' +
                    '<button onclick="deleteText(this)">Delete</button>' +
                    '<button onclick="completeTask(this)">Tick</button>' +
                '</div>' +
            '</div>';
        }
        document.getElementById("anotherPage").style.display = "block";
        var displayArea = document.getElementById("displayText");
        // Insert the new task at the beginning
        displayArea.insertBefore(displayText, displayArea.firstChild);

        // Store tasks in Local Storage
        localStorage.setItem('tasks', JSON.stringify(displayArea.innerHTML));
    }

    function deleteText(element) {
        element.parentNode.parentNode.remove();

        // Update Local Storage after deletion
        localStorage.setItem('tasks', JSON.stringify(document.getElementById("displayText").innerHTML));
    }

    function completeTask(element) {
        var completedText = document.createElement("span");
        completedText.textContent = "Work completed";
        completedText.classList.add("completed");
        element.parentNode.appendChild(completedText);
        element.style.display = "none"; // Hide the tick button after completion

        // Update Local Storage after completion
        localStorage.setItem('tasks', JSON.stringify(document.getElementById("displayText").innerHTML));
    }
</script>

</body>
</html>
