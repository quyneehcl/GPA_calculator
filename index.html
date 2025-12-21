<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>GPA Calculator</title>
<style>
    body{font-family:'Segoe UI',Tahoma,sans-serif;background:#f0f2f5;padding:20px;}
    .container{max-width:1200px;margin:auto;background:white;padding:20px;border-radius:15px;box-shadow:0 5px 15px rgba(0,0,0,0.1);}
    .course-card{background:white;padding:15px;border-radius:12px;margin-bottom:20px;box-shadow:0 2px 8px rgba(0,0,0,0.1);border:1px solid #eee;}
    .course-header{display:flex;justify-content:space-between;align-items:center;margin-bottom:10px;}
    .course-title input{font-size:1.2em;font-weight:bold;border:none;border-bottom:2px solid #667eea;padding:3px 6px;width:200px;}
    .course-credits{width:60px;padding:5px;border:2px solid #667eea;border-radius:5px;text-align:center;}
    .btn{padding:6px 12px;border:none;border-radius:5px;color:white;cursor:pointer; transition: opacity 0.2s;}
    .btn:hover{opacity: 0.8;}
    .btn-primary{background:#667eea;}
    .btn-success{background:#28a745;}
    .btn-danger{background:#dc3545;}
    .btn-info{background:#17a2b8;}
    .btn-small{padding:3px 8px;font-size:0.8em;}
    .task-category{background:#f8f9fa;padding:10px;border-radius:8px;margin-bottom:10px;border-left:4px solid #28a745;}
    .task-category-header{display:flex;justify-content:space-between;align-items:center;margin-bottom:8px;}
    .task-item{display:grid;grid-template-columns:2fr 1fr 1fr 1fr auto;gap:8px;margin-bottom:5px;}
    .task-item input{padding:5px;border:1px solid #ddd;border-radius:5px;width:100%;}
    .final-gpa{padding:20px;background:#28a745;color:white;border-radius:15px;text-align:center;margin-top:20px;}
    .gpa-value{font-size:2.2em;font-weight:bold;margin:0 10px;}
</style>
</head>
<body>

<div class="container">
    <h1>📚 GPA Calculator</h1>
    
    <div style="display:flex;gap:10px;margin-bottom:20px;background:#eef2ff;padding:15px;border-radius:10px;">
        <div>
            <label>Course Name:</label><br>
            <input type="text" id="newCourseName" placeholder="e.g: Calculus I">
        </div>
        <div>
            <label>Credit:</label><br>
            <input type="number" id="newCourseCredits" min="1" max="10" value="3" style="width:60px;padding:5px;">
        </div>
        <button class="btn btn-primary" onclick="addNewCourse()" style="align-self: flex-end;">+ Add Course</button>
        <button class="btn btn-danger" onclick="clearAllData()" style="align-self: flex-end; margin-left: auto;">Delete</button>
    </div>

    <div id="coursesContainer"></div>
    <div id="finalGPADisplay"></div>
</div>

<script>
let courses = [];

// 1. Grade Logic
function percentToLetterGrade(p){
    if(p>=89.5)return'A'; if(p>=84.5)return'A-'; if(p>=79.5)return'B+'; if(p>=74.5)return'B';
    if(p>=69.5)return'B-'; if(p>=64.5)return'C+'; if(p>=59.5)return'C'; if(p>=54.5)return'C-';
    if(p>=49.5)return'D+'; if(p>=44.5)return'D'; return'F';
}
function letterGradeToGPA(letter){
    const map={'A':4,'A-':3.7,'B+':3.3,'B':3,'B-':2.7,'C+':2.3,'C':2,'C-':1.7,'D+':1.3,'D':1, 'D-':0.7,'F':0};
    return map[letter]||0;
}

// 2. Data Persistence (LocalStorage)
function saveData() {
    localStorage.setItem('gpa_data_v2', JSON.stringify(courses));
}

function loadData() {
    const saved = localStorage.getItem('gpa_data_v2');
    if (saved) {
        courses = JSON.parse(saved);
        courses.forEach(course => {
            renderCourseCard(course);
            course.categories.forEach(cat => {
                renderCategory(course.id, cat);
                cat.tasks.forEach(task => renderTask(course.id, cat.id, task));
            });
        });
        updateOverallGPA();
    }
}

function clearAllData() {
    if(confirm("Are you sure you want to delete?")) {
        localStorage.removeItem('gpa_data_v2');
        location.reload();
    }
}

// 3. Core Functions
function addNewCourse(){
    const name = document.getElementById('newCourseName').value.trim();
    const credits = parseFloat(document.getElementById('newCourseCredits').value);
    if(!name || !credits) { alert('Please enter the course name and credit.'); return; }
    
    const course = { id: Date.now(), name: name, credits: credits, categories: [] };
    courses.push(course);
    renderCourseCard(course);
    updateOverallGPA();
    document.getElementById('newCourseName').value = '';
}

function updateCourse(courseId, field, value) {
    const course = courses.find(c => c.id === courseId);
    if (course) {
        course[field] = (field === 'credits') ? (parseFloat(value) || 0) : value;
        updateOverallGPA();
    }
}

function addCategory(courseId){
    const cname = prompt('Component name (e.g., Midterm, Attendance...)');
    const weight = parseFloat(prompt('Weight % (e.g., 30)'));
    if(!cname || isNaN(weight)) return;

    const course = courses.find(c => c.id === courseId);
    const cat = { id: Date.now(), name: cname, weight: weight, tasks: [] };
    course.categories.push(cat);
    renderCategory(courseId, cat);
    updateOverallGPA();
}

function addTask(courseId, catId){
    const course = courses.find(c => c.id === courseId);
    const cat = course.categories.find(c => c.id === catId);
    const task = { id: Date.now(), name: '', score: 0, maxScore: 100, scoreIf: null };
    cat.tasks.push(task);
    renderTask(courseId, catId, task);
    updateOverallGPA();
}

function updateTask(courseId, catId, taskId, field, value) {
    const course = courses.find(c => c.id === courseId);
    const cat = course.categories.find(c => c.id === catId);
    const task = cat.tasks.find(t => t.id === taskId);
    
    if (field === 'scoreIf') {
        task[field] = value !== '' ? parseFloat(value) : null;
    } else if (field === 'name') {
        task[field] = value;
    } else {
        task[field] = parseFloat(value) || 0;
    }
    updateOverallGPA();
}

// 4. Rendering
function renderCourseCard(course){
    const container = document.getElementById('coursesContainer');
    const div = document.createElement('div');
    div.className = 'course-card';
    div.id = `course-${course.id}`;
    div.innerHTML = `
        <div class="course-header">
            <div class="course-title">
                <input type="text" value="${course.name}" oninput="updateCourse(${course.id}, 'name', this.value)">
            </div>
            <div>
                Credit: <input type="number" class="course-credits" value="${course.credits}" oninput="updateCourse(${course.id}, 'credits', this.value)">
                <button class="btn btn-danger btn-small" onclick="removeCourse(${course.id})">🗑️</button>
            </div>
        </div>
        <div style="display:flex; gap:15px; margin-bottom:10px; font-weight:bold; color:#444;">
            <span>% Total: <span class="course-percent">0</span>%</span>
            <span>Grade: <span class="course-letter">-</span></span>
            <span>GPA: <span class="course-gpa">0</span></span>
            <span style="color:#28a745;">What-If: <span class="course-gpa-if">0</span></span>
        </div>
        <div class="categories-container"></div>
        <button class="btn btn-success btn-small" onclick="addCategory(${course.id})">+ Add Score Component</button>
    `;
    container.appendChild(div);
}

function renderCategory(courseId, cat){
    const courseDiv = document.getElementById(`course-${courseId}`);
    const container = courseDiv.querySelector('.categories-container');
    const div = document.createElement('div');
    div.className = 'task-category';
    div.id = `cat-${cat.id}`;
    div.innerHTML = `
        <div class="task-category-header">
            <span><strong>${cat.name}</strong> (${cat.weight}%) - Score: <span class="cat-percent">0</span>%</span>
            <div>
                <button class="btn btn-info btn-small" onclick="addTask(${courseId},${cat.id})">+ Score</button>
                <button class="btn btn-danger btn-small" onclick="removeCategory(${courseId},${cat.id})">🗑️</button>
            </div>
        </div>
        <div class="tasks-container"></div>
    `;
    container.appendChild(div);
}

function renderTask(courseId, catId, task){
    const catDiv = document.getElementById(`cat-${catId}`);
    const container = catDiv.querySelector('.tasks-container');
    const div = document.createElement('div');
    div.className = 'task-item';
    div.id = `task-${task.id}`;
    div.innerHTML = `
        <input type="text" placeholder="Assignment Name" value="${task.name}" oninput="updateTask(${courseId},${catId},${task.id},'name',this.value)">
        <input type="number" placeholder="Score" value="${task.score}" oninput="updateTask(${courseId},${catId},${task.id},'score',this.value)">
        <input type="number" placeholder="Maximum" value="${task.maxScore}" oninput="updateTask(${courseId},${catId},${task.id},'maxScore',this.value)">
        <input type="number" placeholder="What If" value="${task.scoreIf??''}" oninput="updateTask(${courseId},${catId},${task.id},'scoreIf',this.value)">
        <button class="btn btn-danger btn-small" onclick="removeTask(${courseId},${catId},${task.id})">×</button>
    `;
    container.appendChild(div);
}

// 5. Calculations & UI Update
function updateOverallGPA(){
    let totalPoints = 0, totalPointsIf = 0, totalCredits = 0;

    courses.forEach(c => {
        let courseWsum = 0, courseWsumIf = 0, totalWeight = 0;

        c.categories.forEach(cat => {
            let taskSum = 0, taskSumIf = 0, taskMax = 0;
            cat.tasks.forEach(t => {
                taskSum += t.score;
                taskSumIf += (t.scoreIf !== null) ? t.scoreIf : t.score;
                taskMax += t.maxScore;
            });

            const catScore = taskMax > 0 ? (taskSum / taskMax) * 100 : 0;
            const catScoreIf = taskMax > 0 ? (taskSumIf / taskMax) * 100 : 0;
            
            document.getElementById(`cat-${cat.id}`).querySelector('.cat-percent').innerText = catScore.toFixed(1);
            
            courseWsum += catScore * (cat.weight / 100);
            courseWsumIf += catScoreIf * (cat.weight / 100);
            totalWeight += cat.weight;
        });

        const finalPerc = totalWeight > 0 ? (courseWsum / (totalWeight/100)) : 0;
        const finalPercIf = totalWeight > 0 ? (courseWsumIf / (totalWeight/100)) : 0;
        
        const gpa = letterGradeToGPA(percentToLetterGrade(finalPerc));
        const gpaIf = letterGradeToGPA(percentToLetterGrade(finalPercIf));

        totalPoints += gpa * c.credits;
        totalPointsIf += gpaIf * c.credits;
        totalCredits += c.credits;

        const card = document.getElementById(`course-${c.id}`);
        card.querySelector('.course-percent').innerText = finalPerc.toFixed(2);
        card.querySelector('.course-letter').innerText = percentToLetterGrade(finalPerc);
        card.querySelector('.course-gpa').innerText = gpa.toFixed(2);
        card.querySelector('.course-gpa-if').innerText = gpaIf.toFixed(2);
    });

    const finalGPA = totalCredits > 0 ? totalPoints / totalCredits : 0;
    const finalGPAIf = totalCredits > 0 ? totalPointsIf / totalCredits : 0;

    document.getElementById('finalGPADisplay').innerHTML = `
        <div class="final-gpa">
            <h2>🎓 Academic Results</h2>
            <div>Current GPA: <span class="gpa-value">${finalGPA.toFixed(3)}</span></div>
            <div style="margin-top:10px; opacity:0.9">GPA(What-If): <span class="gpa-value">${finalGPAIf.toFixed(3)}</span></div>
            <p>Total: ${courses.length} course | ${totalCredits} credit</p>
        </div>`;
    
    saveData(); // Mỗi lần tính toán xong là tự động lưu
}

// Xóa môn/thành phần
function removeCourse(id){ courses=courses.filter(c=>c.id!==id); document.getElementById(`course-${id}`).remove(); updateOverallGPA(); }
function removeCategory(cId, catId){ 
    const c = courses.find(x=>x.id===cId); 
    c.categories = c.categories.filter(x=>x.id!==catId); 
    document.getElementById(`cat-${catId}`).remove(); 
    updateOverallGPA(); 
}
function removeTask(cId, catId, tId){
    const c = courses.find(x=>x.id===cId);
    const cat = c.categories.find(x=>x.id===catId);
    cat.tasks = cat.tasks.filter(x=>x.id!==tId);
    document.getElementById(`task-${tId}`).remove();
    updateOverallGPA();
}

// Chạy khi vừa mở trang
window.onload = loadData;

</script>
</body>
</html>
